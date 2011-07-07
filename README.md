======

twotoasters/zxing is a fork of just the components needed to include the zxing library in an ios project. The full zxing library includes dozens of platforms and is pretty bloated at 100mb to drop into another project as a submodule, so this fork is just a stripped down copy intended for that purpose

======

Installation instructions (from iphone/README):

1. Locate the "ZXingWidget.xcodeproj" file under "`zxing/iphone/ZXingWidget/`". Drag ZXingWidget.xcodeproj and
   drop it onto the root of your Xcode project's "Groups and Files"  sidebar.  A dialog will
   appear -- make sure "Copy items" is unchecked and "Reference Type" is "Relative to Project"
   before clicking "Add". Alternatively you can right-click on you project navigator and select 'Add files to "MyProject"'  
 
2. Now you need to link the ZXingWidget static library to your project.  To do that,
    a. select you project file in the project navigator
    b. In the second column, select your _target_ and not the project itself  
    c. Go to the 'build phases' tab, expand the 'link binary with libraries' section,
			d. Click the add button A dialog will appear and you should see libZXingWidget.a in the very first possibilities

3. Now you need to add ZXingWidget as a dependency of your project, so Xcode compiles it whenever
	 you compile your project. 
	    a. like in substep c. of previous step, you nedd to do that in the 'build phases' tab of your target
	    b. Expand the 'Target Dependencies' section
	    c. Click the add Button and a dialog will appear select ZXingWidget target

4. Headers search path 1: you need to tell your project where to find the ZXingWidget headers. Select your project in the 
   project navigator, and the select your target and go to the "Build Settings" tab. Look for "Header Search Paths" and double-click
	 it.  Add the relative path from your project's directory to the
	 "zxing/iphone/ZXingWidget/Classes" directory. Make sure you click the checkbox "recursive path" ! 

5. Headers search path 2: You need to add zxing cpp headers to your headers search path, do this similarly as previous step to point the path to cpp/core/src/ where the 'zxing' directory is. You don't need to make this search path recursive so do not check the "recursive path" option

	6. Import the following iOS frameworks: 
	   a. AVFoundation
	   b. AudioToolbox
	   c. CoreVideo
	   d. CoreMedia
	   e. libiconv
	   f. AddressBook
   g. AddressBookUI
	   This must be done by adding them in the 'Link Libraries with Binary' just like step 2.c.

7. You're almost ready to go ..

8. #import <ZXingWidgetController.h> in a source file

9. #import <QRCodeReader.h> for example because you will need to inject a barcode reader into ZXingWidgetController. 

10. MAKE SURE the file in which you are using the code deader is a .mm because you are now silently including some c++ code. If you don't do so then
   the compiler may cry as if it does not find some files !

11. It should work :)
