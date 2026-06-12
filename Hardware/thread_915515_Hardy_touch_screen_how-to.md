---
title: "Hardy touch screen how-to"
date: 2008-09-09
forum: Hardware
---

### Post by djacidjac on 2008-09-09
How to install drivers (egalax_drv.so) and utilities (TouchKit) for EETI (eGalax_eMPIA Technology Inc.) TouchMark USB touch screens in Ubuntu Hardy Heron. 

Disclaimer: I don't know what I'm doing. Use at your own risk.

--This is the driver you want for eeePc wired with a Kidshop touchscreen, AFAIK, thanks for the info alienseer23 at eeeuser.com
--My touch screen is a Touch Mark brand. 
--My tower is a Dell Dimension 4300.

1) Go to [http://210.64.17.162/web20/TouchKitDriver/linuxDriver.htm](http://210.64.17.162/web20/TouchKitDriver/linuxDriver.htm)
2) Download the correct driver for your system. This is an archived file.
3) Extract the archive. (I highly recommend reading the Driver Guide.pdf)
4) Make sure you've gotten rid of any other drivers and utilities you may have attempted to install previously. 
   	(The ones that come with Ubuntu are ok, they will be anticipated by the EETI installer.)
5) Make sure your touch screen is plugged in or otherwise attatched properly.
6) Open a Terminal and navigate to the new directory. (For me it was called TouchKit_x14)
7) type 
	sudo sh setup.sh

   and enter your administrator password. This will run the installer script.

8) BEFORE PROCEEDING THROUGH THE INSTALLATION read the output from the first phase. The installer may give an error that it couldn't copy the driver from a certain directory because it's not there. The installer is looking in the wrong path. If so, open another Terminal without closing the first one. Locate the driver (for me it was /TouchKit_x14/egalax_drv.so) and manually sudo cp it to where the script was trying to put it. (for me it was /usr/lib/xorg/modules/input)
  	 That is, type

	sudo cp PathToWhereYouExtractedTheArchive/TouchKit_x14/egalax_drv.so /usr/lib/xorg/modules/input

	and enter your administrator password. 

9) Finish the installer running in the first Terminal. At this point you can run TouchKit to calibrate and use your touch screen, but it will be buggy and have problems. The following steps fix that. They are described in the Driver Guide.pdf, but their purpose is not explained well (or it's above my head). What this does is prevent a conflict between your mouse and your touch screen.
 
10) In a Terminal type

	cat /proc/bus/input/devices

11) Find your mouse in the devices it lists.

12) Find the "Handler" under your mouse. It will say something like 'HANDLER mouseX eventY' where X and Y are numbers. Take note of X.

13) Back up /etc/X11/xorg.conf . This is not necesry but I highly recomend it. (A simple way to do this is to open it and save-as xorg.conf.bak . This way all you have to do is save-as xorg.conf.bak as xorg.conf and answer "y" to overwrite the version you edited. This leaves your .bak file untouched and is easy to do in a command line if you repeatedly, by accident, mess up your xorg.conf and can't startx.)

14) In a terminal type

	sudo gedit /etc/X11/xorg.conf
	
	and enter your administrator password

15) Locate an entry similar to this for your mouse:

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"Device" "CorePointer"
EndSection

16) Now replace "CorePointer" with "/dev/input/mouseX" where X is the number you read from the output of step 10).

17) Save xorg.conf

18) restart gdm (Ctrl+Alt+BackSpace) or log out and back in, or restart the system.

19) locate and run TouchKit . There is a copy in TouchKit_x14 and the installer also (in my case anyway) places a copy in /usr/lib/xorg/modules/input . It doesn't matter which one you run because it saves it's settings in a seprate file.

20) Perform the 4 point calibration (or the 25 point if you want/need) and hopefully begin using your touch screen!

21) Suggestions:

	a) I suggest making a launcher for TouchKit because it doesn't get added to any menus automatically.

UPDATE: It gets added to the XFCE menu (under "other" I think) but if the touch screen is out of wack I wouldn't want to have to navigate any menus to run the calibrator. I guess you could add it to the gnome menu if you wanted to also. It also comes with a nifty little icon that you can use for the launcher.

 	b) I suggest you check out the on-screen keyboard that comes with Ubuntu Hardy Heron. Go to a Terminal and type: 

	onboard

UPDATE: ...and make a launcher for onboard too! You can have onboard pop up at login, but I haven't found a way to get it up to enter admin passwords yet, so keep a real keyboard handy for those situations.

    	c) I also suggest checking out a program called Xournal. I just got it, but it looks promising.

UPDATE: Xournal is one of the nicest pieces of software I've had the pleasure of using. Now does anyone know of any good hand-writing recognition software for Linux?

Thanks to everyone who posted info on the web! I'll try to return the favors by posting my solutions. :D

---

