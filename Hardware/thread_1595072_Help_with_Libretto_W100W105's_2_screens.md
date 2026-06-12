---
title: "Help with Libretto W100/W105's 2 screens"
date: 2010-10-12
forum: Hardware
---

### Post by PSyMastR on 2010-10-12
So, I am running Ubuntu Netbook Remix 10.10 on my Libretto W105, and I was wondering if there was a way to get the second screen to work, such that I can stick the virtual keyboard (onBoard) on the bottom screen.

Right now it displays nothing and the touchscreen acts reversed to the top screen's touch screen (as in dragging up left goes down right, while on the top screen the touch is perfect).

Also the sound doesn't work.  It uses an onboard Realtek chip, but thats just a minor issue.

I am having trouble figuring this netbook version out (Been using Ubuntu for a long time, and I manage a few servers on it, but damned if I am on this netbook remix haha)

Specs are here:
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/libretto_W105-L251.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/libretto_W105-L251.pdf)

Any suggestions on the screen issue?

---

### Post by PSyMastR on 2010-10-28
I hate to double post, but after 2 weeks, I have yet to find a solution.  Does anyone have any ideas?

---

### Post by wimvd on 2010-11-07
> **PSyMastR said:**
> I hate to double post, but after 2 weeks, I have yet to find a solution.  Does anyone have any ideas?
Hi,

I'm trying to do the same, but also haven't succeeded yet. May be we should combine forces.

Regards,
Wim.

---

### Post by shinsenai on 2010-12-01
Hi, I'm trying the same, but I'm not even getting as far as you do. I can easily run Ubuntu from the Live CD or USB key, but if I try to install it on the disk, it boots in text mode, keeps trying to re-mount the disk from read-only and after a while the upper screen goes blank (the lower never comes up as you also have found). How did you install Ubuntu? I'm using 10.10

Thanks for any suggestion.

Update:
I've found that it is necessary to blacklist the intel_ips module:

[http://ubuntuforums.org/showthread.php?t=1601023](http://ubuntuforums.org/showthread.php?t=1601023)

---

### Post by shinsenai on 2010-12-02
> **PSyMastR said:**
> 
Also the sound doesn't work.  It uses an onboard Realtek chip, but thats just a minor issue.


Hi, in case you haven't already solved it, you can fix the sound problem by adding the following line at the end of the ALSA configuration file /etc/modprobe.b/alsa-base.conf

options snd-hda-intel model=auto

---

### Post by shinsenai on 2010-12-04
An update on this issue. The problem has been reported to the Intel Linux Graphics guys and Chris did his magic. A fix should be available soon:

[http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/2401](http://comments.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/2401)

Cheers,

Alberto

---

### Post by Anfanglir on 2010-12-28
Did you manage to configure the second screen? 

I have just ordered a Libretto w100 10D, and it would be fun to run ubuntu on it.

/ Anfanglir

---

### Post by Anfanglir on 2011-01-03
OK
so my Libretto w100 has arrived and I would like to install ubuntu. Don't know how to fix the second screen though. Judging by the thread shinsenai linked to, some ppl have it up and running. The description isn't detailed enough for a newbie like me to figure out what to do.

Looked around and found another post about a patch for the libretto, but dont know what to do with that info:
[http://article.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/2539/](http://article.gmane.org/gmane.comp.freedesktop.xorg.drivers.intel/2539/)

Any hints?

/ Anfanglir

---

### Post by Anfanglir on 2011-01-05
Just back to report partial progress. I installed the latest daily build of Ubuntu 11.04, and then the new kernel (2.6.37, [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-natty/)) that is supposed to have the fix for the Libretto's second screen. 

The screen now works but mirrors the first one and is diplayed upside down. There may be an easy way to fix this, but 11.04 use Unity instead of Gnome, and I am not familiar with the system yet.

Onboard functions OK as a virtual keyboard once Ubuntu is booted, but for grub menu (and terminal) a usb-keyboard must be used [EDIT: the keyboard-launcher button can be used as down arrow, and bulletin board-launcher button can be used as select. END EDIT]. Besides the virtual keyboard, Win7 have a virtual touchpad, dont know of any equivalent for ubuntu (but please fill me in).

Wifi don't work out of the box, haven't bothered fixing it yet, instead been using a usb-wifi.

/ Anfanglir

---

### Post by Trooper_Max on 2011-01-27
Any further progress here? Sounds like you're getting close Anfanglir.
 
I'm going to be trying this stuff out soon on my Libretto (probably not until Sunday though), I'll let ya'll know how it goes.
 
I also have a Dell Inspiron Duo (I guess I'm a bit of a touch enthusiast :D), and I have been following their progress with Ubuntu and I think there is some stuff learned over there that might carry over here as well:
[http://ubuntuforums.org/showthread.php?t=1658635](http://ubuntuforums.org/showthread.php?t=1658635)
 
Most notably, they found a program (touchscreen-helper) that adjusts the touch-screen inputs so that it functions correctly when you rotate the monitor. I'm not sure it will handle the complications of two touchscreens fully, but it may be a good starting point for making sure the touch inputs work properly.
 
Here's a quote, I've trimmed out the stuff I think is irrelevant to efforts here:
> **Caboose885 said:**
> **TwoFinger Multi-touch touchpad (Optional if you want it)**
Run
```
sudo apt-add-repository ppa:plippo/t101mt
```Then....
```
sudo apt-get update
```Then....```
sudo apt-get install eeepc-touchpad-twofingers
``````
sudo update-grub
```**Rotating the screen properly -- ninjaaron**
```
sudo apt-get install touchscreen-helper
```Then click System-->Preferences-->Monitor to change the screen orientation. If you want you can enable "Show Monitor in panel" to make it easier to rotate on the fly.
```
xrandr -o [normal, inverted, left, right, 0, 1, 2, 3]
```
(the numbers and words are the same thing)
 
**Configuring Firefox --Non.Cents**
 
Go and install this [addon]("https://addons.mozilla.org/en-US/firefox/addon/1250/eula/68777?src=addondetail")
 
I know many people like to use backspace as their back button in Firefox.
 
Open Firefox and type in your URL Bar
```
 about:config
``` and then hit enter.
 
Click "I'll be careful, I promise!"
 
In the search box type in "backspace". Double click on the one result that appears and change the value to 0.
 
[SIZE=4]**Optional Programs to Install** [/SIZE]
**Via Synaptic Package Manager** (Applications &#8594; System &#8594; Synaptic Package Manager)
1. **StartupManager **– Allows you to change the Grub boot menu default selection and reduce the grub default time.
2. **ubuntu-restricted-extras** – Adds special file support. MP3, MP4, AVI, Flash, Java, and more!
3. **VLC **– Lighter and better for less powerful hardware (like the Duo) I can get full 1080P [[COLOR=blue]Big Buck Bunny[/COLOR]]("http://www.bigbuckbunny.org/index.php/download/") to play flawlessly on my Duo using VLC
4. **uTouch **– support for multi-touch. (Like I mentioned before the next kernel should fix our issues)
5. **preload -** caches your most used programs to RAM, therefore causing things to open faster. Such as Terminal and Firefox because you use them often. 
 
**Other Packages**
[[COLOR=blue]Ubuntu Tweak[/COLOR]]("http://launchpad.net/ubuntu-tweak/0.5.x/0.5.9/+download/ubuntu-tweak_0.5.9-1_all.deb") --Allows you to have some more control over your computer using the GUI and not terminal.
 
And here's an excerpt from my post over there on configuring Chrome, mainly check out the links for the useful extensions if you want to use Chrome on a touch device:
> **Trooper_Max said:**
> Also, Chrome has become my browser of choice (there were some things I liked about it when it came out that made it nicer for my preferences than FireFox, though admittedly FireFox has probably since become just as nice for the most part), but I found it to be horrible as a touch browser (making everything smaller around the edges really backfired!). No touch dragging and the worst is those tiny X buttons to close the tabs. Luckily there is a Chrome Touch extension that enables touch dragging (though it is not perfect, make use of the modes it provides, which can be switched between just by tapping the icon in the address bar: full to force touch dragging which won't let you select text, auto to let it try to decide, off to disable it). There's also an extension that lets you double click (or triple click if you prefer) to close tabs, though be aware it is by double-clicking anywhere on the page, not the tab at the top. Also note that these extensions don't work on special chrome pages such as chrome://downloads or chrome://extensions, which is annoying but I'm guessing the Chrome developers didn't want extensions circumventing the special chrome pages. Here are the links to the extensions (these work for me in Windows and Ubuntu):
[http://www.chromeextensions.org/appearance-functioning/chrometouch/](http://www.chromeextensions.org/appearance-functioning/chrometouch/)
[https://chrome.google.com/extensions/detail/megplcpdkmjjoondippkedoaidkeikcm](https://chrome.google.com/extensions/detail/megplcpdkmjjoondippkedoaidkeikcm)

 
Also, extra important on the Libretto is making sure you always have access to an onscreen keyboard:
> **ninjaaron said:**
> At the login screen, click the guy with outstretched arms in the bottom right corner. A tab pops up that says Universal Access or something. Click it. From here a dialogue opens that will allow you to have onboard present at every boot.
 
To get the keyboard at the lock screen, go onboard settings (you may have to edit your menu under "Universal Access" to enable this program). There is an option to "Show onboard when unlocking the screen." On the other hand, you may choose to turn off the password requirement for waking from suspend and hibernate with [Ubuntu Tweak.]("http://ubuntu-tweak.com/downloads/")
 
So there it is.
 
They've also been playing with a program called "unclutter" to make the mouse disappear shortly after clicking (though it does this whether you use a real mouse or tap on the screen):
> **ninjaaron said:**
> 
[QUOTE=Caboose885;10339498]We might not need the accelerometer to work in order to pull it off. The screen and the touchpad are on two different inputs. One is mouse0 and the other is mouse1
 
Maybe a script that says when I use mouse0 the pointer disappears but when I use mouse1 the pointer appears.
 
I found this program called "unclutter" Which is a step in the right direction. It hides the mouse after 5 seconds of not being used. It still appears when you touch but at least it will hide while reading something. I might be able to modify the program to work for us :D
 
Its in Synaptic Package Manager. Just type in the quick search box "unclutter" and install it :D
you can set the time it takes for uncltter to hide the mouse with: ```
unclutter -idle [time in seconds]
```You can set it to 0 if you like, and then the pointer is only visible while you are actually touching the screen, so yo won't see it at all. setting it this low causes some jittery behaviour when using the touchpad. I have mine set to 0.1, so I can see the pointer for a tenth of a second before it disappears, in case I'm having trouble hitting a button.[/QUOTE]
 
They've also noted that even if you're using Ubuntu Netbook Edition 10.10 with Unity, you can still select the regular Gnome environment at the login screen. I think several of them are drifting away from Unity...
 
So hopefully some of that is useful, I'll let ya'll know how things go once I get rolling.
 
~Troop

---

### Post by Trooper_Max on 2011-02-02
Not much of an update; I've just been working with live 10.10 netbook usb's (so second screen doesn't work), but I wanted to note that wifi does in fact seem to work for me, but when I do an actual install I start having weird wifi problems that prevent gnome from even loading... repeated messages at the terminal like it is cycling through wifi channels in an infinite loop or something. So not sure what is up. Also get strange crashes/freezes that may be related to inactivity, but not sure.

Good news is, I think I got an image of the hard drive and recovery thumb drive all backed up now, so I can start experimenting more.

~Troop

---

### Post by Anfanglir on 2011-02-02
Yea no luck here either. Haven't been able to rotate the second screen and the system is unstable so it is frustrating to try to fix the rotation issue while the GUI may stop to respond at any time. I put the instability down to the fact I am using a custom built ubuntu with 2.6.37 kernel. I have noticed that the updated kernels now are at 2.6.38, so maybe 2.6.37 is a dead end.

---

### Post by Anfanglir on 2011-02-03
Tried reinstalling using the current daily build ([http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)), it apparently uses 2.6.38-1. Second screen works from start, but unity is buggy. All applications are accessed through the application folder, and scrolling doesnt work inside the folder so I can only access the first rows of applications. Can't even start terminal (only with ctrl+alt+f1), annoying as hell.

---

### Post by Trooper_Max on 2011-02-03
Yeah, I've tried running some of the daily live ISOs and they do activate the second screen, but seem pretty buggy in general or at least half-baked (as should be expected I suppose). In one of them I did manage to get to the Monitors settings and unchecked the mirror monitors box, and the second screen went to like a blank x screen or something, nothing on it. Interestingly enough when I touched either screen at this point, it clicked on the opposite screen. And yes, the second screen  would show the cursor, but still couldn't do anything useful on it.

I had also tried the alpha live dvd release of natty, but it doesn't activate the second screen correctly (it comes on, but is buggy).

~Troop

---

### Post by Anfanglir on 2011-02-05
I have given up on Unity and instead tried alpha 2's of xubuntu and kubuntu (2.6.38-2 kernel). Both environments seem stable so experimenting isn't such a pain. 

In xubuntu the second screen work as a clone of the first, you can rotate it to get the right position but touch coordinates are messed up on 2nd screen.

In kubuntu it is possible to configure the second screen as a second display positioned below the 1st which is a step forward. However, this messes up touch on both screens, so basicly you need to have an external keyboard and mouse to operate it.

The eeepc fix suggested by Troop might adress this, but so far the plippo ppa don't have debs for Natty, so I haven't been able to try this.

Btw, when fiddling with this it's a good idea to use a usb-hub so you can have multiple external usb devices attached simultanously.

/ Anfanglir

---

### Post by Trooper_Max on 2011-02-06
Good news is I got a working install of Linux Mint (10/Julia, equivalent to Maverick) going on my libretto (I used the Mint4Win installer, similar to Wubi-was a little tricky though). It works with 1 screen and the wireless works, so it all seems pretty good, just only one screen works. Better than the Wubi install of Maverick I tried though, which gets stuck in a loop fiddling with the wifi before bringing up Gnome.

Interestingly enough, in the Monitors preferences, it does show two monitors, but the second one still won't come on. I can uncheck the mirror box to separate them, but the second still doesn't come on and the touchscreen inputs are inverted (touching on the first screen no longer works - but I'm guessing it goes to the other inactive screen, while touching the inactive screen clicks on the active screen, but the inputs are still rotated).

Also, the touchscreen-helper program did not seem to help fix the touch inputs when rotating the monitor in this environment.

Edit: I tried installing the latest kernel release candidate for maverick in my mint install, and while it activates the second screen, it doesn't display properly. ([http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.37-rc2-maverick/))

~Troop

---

### Post by Trooper_Max on 2011-02-10
> **Anfanglir said:**
> I have given up on Unity and instead tried alpha 2's of xubuntu and kubuntu (2.6.38-2 kernel). Both environments seem stable so experimenting isn't such a pain. 

In xubuntu the second screen work as a clone of the first, you can rotate it to get the right position but touch coordinates are messed up on 2nd screen.

In kubuntu it is possible to configure the second screen as a second display positioned below the 1st which is a step forward. However, this messes up touch on both screens, so basicly you need to have an external keyboard and mouse to operate it.

Thanks for the info, I gave Kubuntu and Xubuntu alpha2's a try and they are definitely more useable (been running them live, haven't done an actual install yet-tried wubi but couldn't get it to work, I'm really not a fan of partitioning >_>)

I am guessing the touchscreenhelper program is having trouble either because there are two screens or the touch device is different than the one it was written for (or both).

I pulled down the source and a lot of the code seems to be about managing profiles/settings for different devices. The core of the program really just waits for screen change notify events, looks up the profile for the device in question (or creates a dummy profile), then calibrates the device (using XChangeDeviceProperty to set properties) Here's an excerpt with XChangeDeviceProperty calls:

```
		if(matrixMode) {
			if((sizeof l) == 4) {
				XChangeDeviceProperty(display, dev, XInternAtom(display,
					"Coordinate Transformation Matrix", 0), floatAtom, 32, PropModeReplace, (unsigned char*) matrix, 9);
			} else if((sizeof l) == 8) {
				/* Xlib needs the floats long-aligned, so let's align them. */
				float matrix2[] = { matrix[0], 0., matrix[1], 0., matrix[2], 0.,
				                    matrix[3], 0., matrix[4], 0., matrix[5], 0.,
				                    matrix[6], 0., matrix[7], 0., matrix[8], 0.};
				XChangeDeviceProperty(display, dev, XInternAtom(display,
					"Coordinate Transformation Matrix", 0), floatAtom, 32, PropModeReplace, (unsigned char*) matrix2, 9);
			}
		}

		long calib[] = { minX, maxX, minY, maxY };
		//TODO instead of long, use platform 32 bit type
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axis Calibration", 0), XA_INTEGER, 32, PropModeReplace, (unsigned char*) calib, 4);

		unsigned char flipData[] = {flipHoriz, flipVerti};
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axis Inversion", 0), XA_INTEGER, 8, PropModeReplace, flipData, 2);

		unsigned char cAxesSwap = (unsigned char) axesSwap;
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axes Swap", 0), XA_INTEGER, 8, PropModeReplace, &cAxesSwap, 1);
```

I think it should be possible to set those same properties from the command-line using the "xinput" command. Use "xinput --list" to list devices or "xinput --list [device]" to get more info on a device. Once you are targeting a device use "xinput --list-props [device]" to list the properties like this (on my Dell Inspiron Duo,  not the Libretto right now):

```
troopermax@ubuntu:~$ xinput --list-props 11
Device 'eGalax Inc. USB TouchController':
	Device Enabled (134):	1
	Coordinate Transformation Matrix (136):	1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
	Device Accel Profile (252):	0
	Device Accel Constant Deceleration (253):	1.000000
	Device Accel Adaptive Deceleration (254):	1.000000
	Device Accel Velocity Scaling (255):	10.000000
	Evdev Reopen Attempts (251):	10
	Evdev Axis Inversion (299):	0, 0
	Evdev Axis Calibration (300):	0, 4095, 0, 4095
	Evdev Axes Swap (301):	0
	Axis Labels (302):	"Abs X" (297), "Abs Y" (298)
	Button Labels (303):	"Button Left" (137), "Button Unknown" (296), "Button Right" (139), "Button Wheel Up" (140), "Button Wheel Down" (141)
	Evdev Middle Button Emulation (304):	2
	Evdev Middle Button Timeout (305):	50
	Evdev Wheel Emulation (306):	0
	Evdev Wheel Emulation Axes (307):	0, 0, 4, 5
	Evdev Wheel Emulation Inertia (308):	10
	Evdev Wheel Emulation Timeout (309):	200
	Evdev Wheel Emulation Button (310):	4
	Evdev Drag Lock Buttons (311):	0

```

So I'm guessing with enough fiddling with those settings using the xinput command to set the properties for the devices, we should be able to fix the touchscreen inputs. Once we figure it out, we may be able to add a profile to the touchscreen-helper program or tweak it to work for us or develop a new script/program. I kinda wonder if anyone has written a GUI config tool for xinput though...

I'm too tired to crack out the Libretto and fiddle with this now though, so let me know if anyone else figures this out.

Here's the entire calibration function for reference, in case anyone needs to see more of the matrix stuff:

```
void setCalibration(int id, int minX, int maxX, int minY, int maxY, int axesSwap, int screenWidth, int screenHeight, int outputX, int outputY, int outputWidth, int outputHeight, int rotation) {

	float matrix[] = { 1., 0., 0.,    /* [0] [1] [2] */
	                   0., 1., 0.,    /* [3] [4] [5] */
	                   0., 0., 1. };  /* [6] [7] [8] */

	int matrixMode = 0;
	/* Check if transformation matrix is supported */
	long l;
	if((sizeof l) == 4 || (sizeof l) == 8) {
		/* We only support matrix mode on systems where longs are 32 or 64 bits long */
		Atom retType;
		int retFormat;
		unsigned long retItems, retBytesAfter;
		unsigned char * data = NULL;
		if(XIGetProperty(display, id, XInternAtom(display,
				"Coordinate Transformation Matrix", 0), 0, 9 * 32, False, floatAtom,
				&retType, &retFormat, &retItems, &retBytesAfter,
				&data) != Success) {
			data = NULL;
		}
		if(data != NULL && retItems == 9) {
			matrixMode = 1;
		}
		if(data != NULL) {
			XFree(data);
		}
	}	

	unsigned char flipHoriz = 0, flipVerti = 0;

	if(matrixMode) {	

		if(debugMode) printf("Use matrix method\n");

		/* Output rotation */
		if(rotation & RR_Rotate_180) {
			matrix[0] = -1.;
			matrix[4] = -1;
			matrix[2] = 1.;
			matrix[5] = 1.;
		} else if(rotation & RR_Rotate_90) {
			matrix[0] = 0.;
			matrix[1] = -1.;
			matrix[3] = 1.;
			matrix[4] = 0.;

			matrix[2] = 1.;
		} else if(rotation & RR_Rotate_270) {
			matrix[0] = 0.;
			matrix[1] = 1.;
			matrix[3] = -1.;
			matrix[4] = 0.;

			matrix[5] = 1.;
		}

		/* Output Reflection */
		if(rotation & RR_Reflect_X) {
			matrix[0]*= -1.;
			matrix[1]*= -1.;
			matrix[2]*= -1.;
			matrix[2]+= 1.;
		}
		if(rotation & RR_Reflect_Y) {
			matrix[3]*= -1.;
			matrix[4]*= -1.;
			matrix[5]*= -1.;
			matrix[5]+= 1.;
		}

		/* Output Size */
		float widthRel = outputWidth / (float) screenWidth;
		float heightRel = outputHeight / (float) screenHeight;
		matrix[0] *= widthRel;
		matrix[1] *= widthRel;
		matrix[2] *= widthRel;
		matrix[3] *= heightRel;
		matrix[4] *= heightRel;
		matrix[5] *= heightRel;

		/* Output Position */
		matrix[2] += outputX / (float) screenWidth;
		matrix[5] += outputY / (float) screenHeight;

	} else {

		if(debugMode) printf("Use legacy method\n");

		/* No support for transformations, so use legacy method */

		if(rotation & RR_Rotate_180) {
			flipHoriz = !flipHoriz;
			flipVerti = !flipVerti;
	
		} else if(rotation & RR_Rotate_90) {
			flipVerti = !flipVerti;
			axesSwap = !axesSwap;
		} else if(rotation & RR_Rotate_270) {
			flipHoriz = !flipHoriz;
			axesSwap = !axesSwap;
		}

		/* Output Reflection */
		if(rotation & RR_Reflect_X) {
			flipHoriz = !flipHoriz;
		}
		if(rotation & RR_Reflect_Y) {
			flipVerti = !flipVerti;
		}


		if(axesSwap) {
			swap(&maxX, &maxY);
			swap(&minX, &minY);
		}

		int leftSpace, rightSpace, topSpace, bottomSpace;
		leftSpace = outputX;
		rightSpace = screenWidth - outputX - outputWidth;

		topSpace = outputY;
		bottomSpace = screenHeight - outputY - outputHeight;

		if(flipHoriz) swap(&leftSpace, &rightSpace);
		if(flipVerti) swap(&topSpace, &bottomSpace);
		
		float fctX = ((float) (maxX - minX)) / ((float) outputWidth);
		float fctY = ((float) (maxY - minY)) / ((float) outputHeight);
		minX = minX - (int) (leftSpace * fctX);
		maxX = maxX + (int) (rightSpace * fctX);
		minY = minY - (int) (topSpace * fctY);
		maxY = maxY + (int) (bottomSpace * fctY);

	}

	XDevice *dev = XOpenDevice(display, id);
	if(dev) {
		if(matrixMode) {
			if((sizeof l) == 4) {
				XChangeDeviceProperty(display, dev, XInternAtom(display,
					"Coordinate Transformation Matrix", 0), floatAtom, 32, PropModeReplace, (unsigned char*) matrix, 9);
			} else if((sizeof l) == 8) {
				/* Xlib needs the floats long-aligned, so let's align them. */
				float matrix2[] = { matrix[0], 0., matrix[1], 0., matrix[2], 0.,
				                    matrix[3], 0., matrix[4], 0., matrix[5], 0.,
				                    matrix[6], 0., matrix[7], 0., matrix[8], 0.};
				XChangeDeviceProperty(display, dev, XInternAtom(display,
					"Coordinate Transformation Matrix", 0), floatAtom, 32, PropModeReplace, (unsigned char*) matrix2, 9);
			}
		}

		long calib[] = { minX, maxX, minY, maxY };
		//TODO instead of long, use platform 32 bit type
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axis Calibration", 0), XA_INTEGER, 32, PropModeReplace, (unsigned char*) calib, 4);

		unsigned char flipData[] = {flipHoriz, flipVerti};
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axis Inversion", 0), XA_INTEGER, 8, PropModeReplace, flipData, 2);

		unsigned char cAxesSwap = (unsigned char) axesSwap;
		XChangeDeviceProperty(display, dev, XInternAtom(display,
			"Evdev Axes Swap", 0), XA_INTEGER, 8, PropModeReplace, &cAxesSwap, 1);

		XCloseDevice(display, dev);
	}
}
```

All code excerpted in this post is from touchscreen-helper.c and is:
```
/*
 Copyright (C) 2010, Philipp Merkel <linux@philmerk.de>

 Permission to use, copy, modify, and/or distribute this software for any
 purpose with or without fee is hereby granted, provided that the above
 copyright notice and this permission notice appear in all copies.

 THE SOFTWARE IS PROVIDED "AS IS" AND THE AUTHOR DISCLAIMS ALL WARRANTIES WITH
 REGARD TO THIS SOFTWARE INCLUDING ALL IMPLIED WARRANTIES OF MERCHANTABILITY AND
 FITNESS. IN NO EVENT SHALL THE AUTHOR BE LIABLE FOR ANY SPECIAL, DIRECT,
 INDIRECT, OR CONSEQUENTIAL DAMAGES OR ANY DAMAGES WHATSOEVER RESULTING FROM
 LOSS OF USE, DATA OR PROFITS, WHETHER IN AN ACTION OF CONTRACT, NEGLIGENCE OR
 OTHER TORTIOUS ACTION, ARISING OUT OF OR IN CONNECTION WITH THE USE OR
 PERFORMANCE OF THIS SOFTWARE.
 */
```

~Troop

---

### Post by Trooper_Max on 2011-02-10
Almost got it figured out. Running Kubuntu alpha2, I set the second monitor to be positioned below the first. This of course messed up the touchscreen coordinates, so I went to the terminal to fix it. Here's the process I went through:

***"xinput list"*** shows the touch devices as "Wacom ISDv4 E2 Finger touch" with id's 12 and 13.

***"xinput list-props 12"*** shows the properties for the first touchscreen.
[I]
**"xinput set-prop 12 125 0"**[/I] sets the Device Enabled property for the first touchscreen to 0 (off)
***"xinput set-prop 13 125 0"*** sets the Device Enabled property for the second touchscreen to 0 (off)

***"xinput set-prop 12 125 1"*** to re-enable the first touchscreen and verified by tapping on the top screen that it is indeed the first screen. Noticed that the x coordinate is correct, but the y coordinate is twice what it should be.

***"xinput set-prop 12 127 1, 0, 0, 0, 0.5, 0, 0, 0, 1"*** sets the transformation matrix to scale the y coordinate by half. Doing this almost corrects it.

***"xinput test 12"*** puts the terminal in a loop and outputs the events... when I tap the top screen, it triggers a motion event at the correct coordinates, followed by a button press at the untransformed/incorrect coordinates just as if the matrix hadn't been applied, followed by a button release at the correct coordinates.

***"xinput set-prop 13 125 1" ***re-enables the second touchscreen.
***"xinput set-prop 13 127 -1, 0, 1, 0, -0.5, 1, 0, 0, 1"*** similarly almost fixes the second screen, but it has the same problem.

For reference, ***"xinput set-prop [device] 127 A, B, C, D, E, F, G, H, I"*** corresponds to the matrix:
[FONT=Courier New][A][D][G]
[B][E][H]
[C][F][I][/FONT]

**Cheatsheet for transformations:**
A = X scale
B = X skew
C = X offset

D = Y skew
E = Y scale
F = Y offset

G=H=0
I=1

This is a pretty good reference too, but there are plenty of others:
[http://www.senocular.com/flash/tutorials/transformmatrix/](http://www.senocular.com/flash/tutorials/transformmatrix/)

Probably easier to just base it off the code above though.

**So if we could just figure out why the press event isn't getting transformed, we'd be set.**

I did notice that when I did ***"xinput list"*** an "ImPS/2 Generic Wheel Mouse" also showed up, but disabling it didn't help anything.

Maybe if we search around we'll be able to find other people who have had wacom issues or some wacom tools to help fix this (I think I saw mention of a tool to help calibrate wacom pads somewhere...).

EDIT: Works similarly in Xubuntu alpha 2, same problem. Also, here's the xrandr commands to adjust the bottom screen: (might be easier than finding the options under the different environments you may not be as familiar with)
***xrandr --output LVDS2 --orientation inverted --below LVDS1***

~Troop

---

### Post by Anfanglir on 2011-02-10
good work. It will be few days or a week before I have time to try anything on my end, by then I bet you've got it all figured out ;)

---

### Post by Trooper_Max on 2011-02-14
> **Anfanglir said:**
> good work. It will be few days or a week before I have time to try anything on my end, by then I bet you've got it all figured out ;)

I went away for a few days myself >_>

So I haven't been able to do much more with it, but I did find that there's also an "xsetwacom" command, just haven't figured out if it's useful here...

Thinking of making a separate post to try to call attention to and hopefully resolve the lack of transformation issue. Just made one here:
[http://ubuntuforums.org/showthread.php?t=1687819](http://ubuntuforums.org/showthread.php?t=1687819)

~Troop

---

### Post by Trooper_Max on 2011-03-04
So no real progress here... haven't had much time for it, and the few times I sit and want to work on it, it keeps freezing on me. It didn't normally do this, but has in the past... it's a very characteristic hard freeze where everything locks up and then the fan ramps up to full blast. I don't think it's overheating or anything, because the fan does seem to work and it doesn't even get hot a lot of the times that it does this. It could be my imagination, but I think it seems to happen more while running on battery... guessing it's gotta be something with the Intel stuff.... prolly thermal management.

Anybody else had this problem? Though I saw something somewhere about blacklisting intel_ips and I think I did that, but still being frustrating...

And no love on the other threads I started regarding the touchscreen. Started another one with a more developmental question about getting to be able to use a touchscreen as a touchpad, but no replies:
[http://ubuntuforums.org/showthread.php?t=1698789](http://ubuntuforums.org/showthread.php?t=1698789)

I think it'd be great to be able to have the second screen function as a touchpad when off (maybe use the right/home button as a right mouse button and tap for left). Then press the left/keyboard button and the second screen comes on with a maximized keyboard. Maybe if the hold left mouse button to simulate right-click feature worked better (in my experience it doesn't work sometimes, probably because I haven't been using the plain Gnome desktop and been using Unity), the right button could switch it to a custom launcher for the second screen. Starts to resemble what Toshiba did for Windows, but I think it could be better... I particularly like the second screen off as touchpad idea for some reason... hoping it would save battery too I guess.

~Troop

---

### Post by arobase40 on 2011-09-10
Anyone knows what is the touchscreen module used by Libretto W100/W105 ???

---

### Post by kkcheong on 2011-11-22
> **PSyMastR said:**
> So, I am running Ubuntu Netbook Remix 10.10 on my Libretto W105, and I was wondering if there was a way to get the second screen to work, such that I can stick the virtual keyboard (onBoard) on the bottom screen.

Right now it displays nothing and the touchscreen acts reversed to the top screen's touch screen (as in dragging up left goes down right, while on the top screen the touch is perfect).

Also the sound doesn't work.  It uses an onboard Realtek chip, but thats just a minor issue.

I am having trouble figuring this netbook version out (Been using Ubuntu for a long time, and I manage a few servers on it, but damned if I am on this netbook remix haha)

Specs are here:
[http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/libretto_W105-L251.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/libretto_W105-L251.pdf)

Any suggestions on the screen issue?
Hi there. I also facing the same problem. Even with new Ubuntu, I can't turn on the 2nd screen. And 2nd screen act inverse touch screen. 

Have you found any solution?

---

### Post by roguescholar on 2012-02-11
hey guys, had my libretto for a while now and been following the progress of the 7 or so individuals whove tried to run linux and finally worked  out a quick and dirty solution for the screen orientation, so hope this helps (no need to install  anything but you should be able to run basic shell commands. :) 

special thanks to Trooper_max if I hadnt stumbled on your post Id still be running windows 32bit :(


run:

xrandr

should say both LVDS1&2 are connected, if LVDS2 reports disconnected, youll need to patch your i915 driver to continue
 if  all is good, then run:

xrandr --output LVDS2 --mode 1024x600 --rotate inverted --below LVDS1


now run

xinput list

should  comeup with two entries for "wacom ISDv4 E2 Finger touch" devices. eg ID 11(top screen) & 12(bottom screen) ID's will be higher or lower depending on whats plugged into usb.

now issue xsetwacom commands as follows:

xsetwacom set "12" rotate half

xsetwacom set "11" maptooutput LVDS1

xsetwacom set "12" maptooutput LVDS2



these settings wont survive reboot, and depending on what you plug in from boot to boot the ID's will change, Ive written a script to automate things.

now im  just looking to see if i can find what input method the accelerometers using . Ive checked the "toshiba input device" events with xinput --test and seems to catch both the keyboard button and the home button, but theeeeeeers abit more work to do.
 ill check back soon to see if anyones been bothered continuing :popcorn:

Ill upload the libretto.sh script to save some time.

Enjoy

---

