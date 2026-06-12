---
title: "HOWTO --- Alps/Synaptics Touchpad"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by smeager on 2005-11-02
This is a small HowTo for the troublesome Touchpad problems with Breezy:

First you'll need to download the current synaptics driver ver 0.14.3 from [http://web.telia.com/~u89404340/touchpad/files/]("http://web.telia.com/~u89404340/touchpad/files/").  Then unpack it to a directory of your choosing

> $ tar jxf synaptics-0.14.3.tar.bz2 

Next you'll need to install the following packages if you have not done so already.
x-dev, libx11-dev and libxext-dev

> sudo apt -get install x-dev libx11-dev libxext-dev

Once the packages are install you need to compile the new synaptics driver.

> $ cd {directory of upacked tar file}
make

You may or may not receive syntax errors but these can be ignored as long as it creates the new driver (in bold)
> rm -f **synaptics_drv.o**
ld -r  synaptics.o ps2comm.o eventcomm.o psmcomm.o alpscomm.o -o synaptics_drv.ogcc -O2 -pedantic -Wall -Wpointer-arith -fno-merge-constants -fno-pic -DVERSION="\"0.14.3\"" -IXincludes/usr/X11R6/include -c -o synclient.o synclient.c
gcc -o synclient synclient.o -lm
gcc -O2 -pedantic -Wall -Wpointer-arith -fno-merge-constants -fno-pic -DVERSION="\"0.14.3\"" -IXincludes/usr/X11R6/include -c -o syndaemon.o syndaemon.c
In file included from syndaemon.c:20:
/usr/include/X11/Xlib.h:3575: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3580: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3593: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3606: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3611: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3843: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3847: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3859: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3887: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3891: error: syntax error before ‘_X_SENTINEL’
/usr/include/X11/Xlib.h:3931: error: syntax error before ‘_X_SENTINEL’
make: *** [syndaemon.o] Error 1


Next you can either do a "make install" (which will put the driver into the correct directory) or you can move it yourself with the following command

> $sudo mv /{driver dirctory}/synaptics_drv.o /usr/X11R6/lib/modules/input

Now you are going to have to update you Xorg.conf but first make a back up (just in case)

> $ sudo gedit /etc/X11/xorg.conf

You will need to add the following comments to your Xorg.conf (make it look something like this)

> Section "InputDevice"
	Identifier	"Mouse0"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "InputDevice"
	Identifier  	"Synaptics Touchpad"
  	Driver		"synaptics"
	#Option		"CorePointer"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	#Option		"Device"		"/dev/mouse1"
	Option		"Protocol"		"auto-dev"
	Option		"SHMConfig"		"on"
	Option		"LeftEdge"		"120"
	Option		"RightEdge"		"830"
	Option		"TopEdge"		"120"
	Option		"BottomEdge"		"600"
	Option		"FingerLow"		"25"
	Option		"FingerHigh"		"30"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"MaxDoubleTapTime"	"180"
	Option		"ClickTime"		"100"
	Option		"FastTaps"		"1"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"10"
	Option		"HorizScrollDelta"	"20"
	Option		"MinSpeed"		"0.2"
	Option		"MaxSpeed"		"2.5"
	Option		"AccelFactor"		"0.06"
	Option		"EdgeMotionMinZ"	"30"
	Option		"EdgeMotionMaxZ"	"160"
	Option		"EdgeMotionMinSpeed"	"15"
	Option		"EdgeMotionMaxSpeed"	"15"
	Option		"EdgeMotionUseAlways"	"0"
	Option		"UpDownScrolling"	"1"
	Option		"LeftRightScrolling"	"1"
	Option		"TouchpadOff"		"0"
	Option		"GuestMouseOff"		"1"
	Option		"LockedDrags"		"1"
	Option		"RTCornerButton"	"0"
	Option		"RBCornerButton"	"0"
	Option		"LTCornerButton"	"2"
	Option		"LBCornerButton"	"2"
	Option		"TapButton1"		"1"
	Option		"TapButton2"		"1"
	Option		"TapButton3"		"3"
	Option		"CircularScrolling"	"0"
	Option		"CircScrollDelta"	"0.08"
	Option		"CircScrollTrigger"	"0"
	Option		"CircularPad"		"0"
	Option		"PalmDetect"		"1"
	Option		"PalmMinWidth"		"10"
	Option		"PalmMinZ"		"200"
	Option		"CoastingSpeed"		"0"


> Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Mouse0"   			    		
        InputDevice	"Synaptics Touchpad" 

Save your new Xorg.conf and restart X and you will have a fully finctional Touchpad. Good luck.

---

