---
title: "915resolution not needed in Feisty"
date: 2007-04-23
forum: Hardware &amp; Laptops
---

### Post by Surgeon General on 2007-04-23
welp, finally made it to Feisty and one of the nice things i liked is that i no longer needed 915resolution. "sudo apt-get install xserver-xorg-video-intel" fixed my resolution problem. :guitar:

---

### Post by scotttkd on 2007-04-23
omg...i could kiss you right now!!!!!  I have been killing myself trying to get my external monitor to be recognized while my micro pc is in dock so I tried your solution and viola!  I have external video!!!

woooohoooooo!

many thanks:lolflag:

---

### Post by Surgeon General on 2007-04-24
glad my solution worked for others too. :-D

---

### Post by brettr on 2007-04-24
Quick question, What is the difference between the "xserver-xorg-video-intel" driver and the i810 video driver? I have a VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML card, and i never had to use 915resolution.

---

### Post by ppan76 on 2007-04-24
yes the intel drivers will fix the resolution problems...but with the intel drivers I cannot resume from suspend.
With the i810 drivers I am able to do it.
Can anybody do it?

---

### Post by Syke on 2007-04-24
915resolution is for when you have non-standard resolutions that aren't detected correctly. If you use normal resolutions like 640x480, 800x600, and 1024x768, you'll probably not need 915resolution.

---

### Post by jellystones on 2007-04-24
I still need to package in feisty to let me use my laptop widescreen resolutions

I have the intel 950 video card.

---

### Post by Chris The Ninja Pirate on 2007-04-25
For my Intel 855GM I can now boot with my laptop closed to an external screen but it displays in 1024x768 still, whereas I require 1440x900. I tried selecting another resolution but I just got a blank screen.

New to linux but I have been tearing my hair out for several days using 915resolution and xorg-edit to allow me to output 1440x900. I was hoping this would be the answer.

Anyone able to help a beginner with what I need to add to 915resolution and xorg.conf to allow me to output 1440x900 using the driver linked to above rather than the i810 driver?

---

### Post by Surgeon General on 2007-04-25
have you tried "sudo apt-get install xserver-xorg-video-intel" already? it worked with scotttkd and since you said you have an Intel 855GM chipset try it.

---

### Post by Chris The Ninja Pirate on 2007-04-25
> **Surgeon General said:**
> have you tried "sudo apt-get install xserver-xorg-video-intel" already? it worked with scotttkd and since you said you have an Intel 855GM chipset try it.

Yeah sorry, should have been more specific. I tried the intel driver rather than the i810 and it gave me two new resolutions (1280x1280 and 863x642(!!!!)) and a choice of refresh rates, and allowed me to boot the laptop with the lid closed when connected to my monitor which it failed on before. If I look in my xorg.conf it still lists i810 as the driver in the screen configuration but not sure if that is the problem. Jellystones inferred that he had to carry out further steps to get it to work with his widescreen monitor.

---

### Post by Surgeon General on 2007-04-25
Check this out [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)

---

### Post by ppan76 on 2007-04-25
I am not sure if you are aware of this. but sometimes you have to change the driver in xorg.conf manually.

Search the line that says "i810" and replace it for "intel"

When I install the drivers and I had to do this.

---

### Post by ]Nbx*cmD[ on 2007-04-26
Hi!

I had 915resolution working, I've got an Intel i950 chipset card and it worked pretty ok except for the fullscreen apps and some other issues, so i decided to try out the intel driver. For my surprise, though, it didn't work, gdm comes out and when i enter my username and password it just restarts gdm again.
I checked dmesg and there's nothing there, of course i changed the driver to "intel" and uninstalled 915 resolution... any solution?

Now i'm using the i850 driver again, but i'd love to solve that minor issues!

Thanks!

---

### Post by extremecarver on 2007-04-26
For me the new intel driver is not yet usable as external monitor will only work on clone mode so either 1280x800 (completely wrong picture on 4/3 aspect CRT) or 1024x768.  

did anyone manage to have an external monitor working in 4/3 with higher resolution than inbuilt laptop screen for 16/9 or 16/10 laptops?

---

### Post by Chris The Ninja Pirate on 2007-04-26
> **Surgeon General said:**
> Check this out [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_enable_Large_Widescreen_Support)

Cheers for that but I have something like this in my xorg.conf already.

#Section "Monitor"

#	Identifier "Video7"

#	HorizSync 30-82

#	VertRefresh 56-75

#	DisplaySize 270 203

#	Modeline "1440x900_60.00" 106.47 1440 1520 1672 1904 900 901 904 932 -HSync +Vsync

#EndSection

I am missing the DPMS option, not sure if that is significant. I generated the modeline using xorg-edit (a total bonus for me since every edit I did to the xorg.conf before killed the xserver!)

Also the new driver has removed my ability to switch between screens with a Fn+F5 switch, which the old i810 driver allowed. Not sure if I can now install i810switch?

I have (hopefully) attached my xorg.conf to this post. As ppan76 notes my Device is still showing as i810, so I am going to try changing this to intel as suggested and see what happens.

---

### Post by Chris The Ninja Pirate on 2007-04-26
EDIT - Sadly changing the driver to intel has not changed anything. I also include my xorg.0.log file if anyone feels like having a look. The only thing that looks out of place is if you have a look towards the end of all the screen loading stuff it would seem to think it has something bound to both pipe A and pipe B of the GPU - I had a feeling when I was messing around with the i810 driver when the laptop was closed nothing showed as being attached to pipe A? I know less though.

---

### Post by Surgeon General on 2007-04-26
i never manually edited xorg.conf this time. here's part of my xorg.conf. seems this "unstable" driver is stable enough for me:

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by Chris The Ninja Pirate on 2007-04-27
I have had a friend who is far more experienced with linux have a look at the system for me and he couldn't find anything obviously wrong with what I was doing. He is going to do a bit of digging and see what he can turn up.

Just out of interest is anyone able to boot a laptop with an Intel GPU with the screen closed with an external widescreen LCD attached and have it boot and display correctly on the external LCD? Maybe I am just trying to do something that is a bit unusual?

---

### Post by extremecarver on 2007-04-27
Booting with laptop screen turned off works for me (well changing the monitor with FN-F8 and thereby switching to external monitor before entering grub as my monitor allways switches on and off when lid is closed).

I went back to i810 though. Waiting eagerly for x.org 7.3 which hopefully solves many x issues.

---

### Post by rohandhruva on 2007-04-27
That worked perfectly on my Acer TravelMate 3260, having intel GMA 950 card. Since I don't use any external monitor, I don't have any issues with it .. Great work !

---

### Post by Chris The Ninja Pirate on 2007-04-27
> **extremecarver said:**
> Booting with laptop screen turned off works for me (well changing the monitor with FN-F8 and thereby switching to external monitor before entering grub as my monitor allways switches on and off when lid is closed).

I went back to i810 though. Waiting eagerly for x.org 7.3 which hopefully solves many x issues.

> **rohandhruva said:**
> That worked perfectly on my Acer TravelMate 3260, having intel GMA 950 card. Since I don't use any external monitor, I don't have any issues with it .. Great work !

Hmmm, perhaps it is due to my Intel 855 or the particular hardware configuration in my Acer TM302. X.org 7.3 is some time away isn't it?

---

### Post by schmolch on 2007-04-27
With intel i am no longer able to rotate the screen which is a crucial feature for me cause i use a tablet-pc.

---

### Post by derekguy on 2007-05-13
I changed to the intel driver

```
sudo aptitude install xserver-xorg-video-intel
```

```
sudo gedit /etc/X11/xorg.conf
```

I changed the driver from "i810" to "intel"

Nothing crashed :) My Beryl seems smoother but slower :confused: 

Perhaps it is just me.

Thankyou for the howto.

I am still unable to get my S-Video out working (VGA out is untested too) can anyone point me to a thread? I am searching at the moment.

I am using a Compaq Presario B1800 with Intel Pentium M (2.0GHz) and integrated Intel Graphics (Mobile 915GM/GMS/910GML Express Graphics Controller)

Cheers for any help, Derek

---

### Post by russbuss on 2007-05-17
Wow, thanks to everyone who made all of this happen.  I've had a wide-screen Acer monitor (AL916W) I've been dying to use but nothing has ever allowed me to get 1440x900 resolution.

```
sudo apt-get install xserver-xorg-video-intel
```

followed be a restart did the trick.

I did have to go to System->Preferences->Screen Resolution to select 1440x900, but I mention this just so other folks realize that the updated drivers won't auto-detect the screen resolution for you.

Thanks again!!!!!

---

### Post by yey365 on 2007-05-18
Great post and the install worked a charm, after editing xorg.conf from Driver "i810" to "intel" (without the quotes.  The added bonus is that suspen now work as you want it to and doesn't fail to resume.  Thanks,

Jim

---

### Post by ianseballe on 2007-05-22
thanks man!

this post should be "sticky-ed." 

took me hours just to find this divine providence!

---

### Post by veloce on 2007-05-25
> **ianseballe said:**
> thanks man!

this post should be "sticky-ed." 

took me hours just to find this divine providence!

Anyone get dual monitors working with the intel driver?  I've had to go back to i810.

---

### Post by extremecarver on 2007-05-25
> **veloce said:**
> Anyone get dual monitors working with the intel driver?  I've had to go back to i810.
Me neiter, Dual Monitor is for me the reason to use i810 (already external monitor alone is not working properly with video-intel)

---

### Post by Ripfox on 2007-05-26
@ derekguy

[http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+monitor](http://ubuntuforums.org/showthread.php?t=361124&highlight=dual+monitor)

This works for me but only with the i810 atm.

---

### Post by phazeman on 2007-05-27
thanks much ! i'm going to try it out tonight !

---

### Post by H.E. Pennypacker on 2007-05-29
It looks like the Intel driver did nothing for me. It may have actually caused problems (in the screen turning on and off).  I've gone back to the i810 driver.

As the OP said, 915resolution is indeed not needed.

---

### Post by Svip on 2007-06-04
Uh, it did kinda work, except... now everytime an application wants fullscreen or I attempt to change resolution, X crashes.

I am using an i810.  I'd really like to get some applications in fullscreen.

---

### Post by veloce on 2007-06-04
> **Svip said:**
> Uh, it did kinda work, except... now everytime an application wants fullscreen or I attempt to change resolution, X crashes.

I am using an i810.  I'd really like to get some applications in fullscreen.

Is this a statement or a question or a request for help? :)

What worked?  What hardware are you using? What version of Ubuntu?  ...

---

### Post by Svip on 2007-06-05
> **veloce said:**
> Is this a statement or a question or a request for help? :)

What worked?  What hardware are you using? What version of Ubuntu?  ...

It's a cry for help!

I have an i810 graphics card, and I use Feisty.

As for what worked, well... having it in 1280x800 resolution, any other resolution made X crash.

---

### Post by veloce on 2007-06-05
> **Svip said:**
> It's a cry for help!

I have an i810 graphics card, and I use Feisty.

As for what worked, well... having it in 1280x800 resolution, any other resolution made X crash.

If you are not using dual monitors, then upgrade to the intel driver and uninstall 915resolution:

the package for the intel driver is:

xserver-xorg-video-i810

So use synaptic package manager to make these changes.

Then use CTL+ALT+F2 to bring up the run command window and edit the xorg.conf file:

```
sudo gedit /etc/X11/xorg.conf
```

Change the reference to "i810" to "intel"

Restart X (CTL+ALT+Bksp)

---

### Post by gharbeia on 2007-08-20
I uninstalled 915resolution then installed xserver-xorg-video-intel (aptitude uninstalls
 xserver-xorg-video-i810 in the process) and changed all the "i810" to "intel" in xorg.
conf. X crashes on Acer Travelmate 3004WTMi.

Any clues?

---

### Post by Carb on 2007-08-21
I would like to thank you for this SOLUTION to my problem.

I have a Gateway M305CRV Laptop with Intel 852/855 chipset.

It works very well for me and my laptop

Carb

---

### Post by spytek on 2007-08-26
This works great thanks.... one thing though....

I'm using an external monitor with 1440x900 resolution, with my laptop screen (1280x800).

Since installing this  intel driver both my external monitor and laptop screen are cloned... which is great... except the laptop screen is using the resolution of the external monitor (1440x900) and not 1280x800... how can I get the laptop screen to use its proper resolution when the external monitor is plugged in???

Here is my current xorg.conf..... THANKS!!!!

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/fonts/X11/misc"
	FontPath	"/usr/share/fonts/X11/cyrillic"
	FontPath	"/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath	"/usr/share/fonts/X11/Type1"
	FontPath	"/usr/share/fonts/X11/100dpi"
	FontPath	"/usr/share/fonts/X11/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x800"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x800"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by kristofer on 2007-08-27
I've got a dell latitude d610, I just installed xserver-xorg-video-intel again.. I've been fighting getting the custom resolution (1400x1050) to work since I bought the machine months ago. Any advice is welcome :)

---

### Post by Schnoidz on 2007-09-06
> **russbuss said:**
> Wow, thanks to everyone who made all of this happen.  I've had a wide-screen Acer monitor (AL916W) I've been dying to use but nothing has ever allowed me to get 1440x900 resolution.

```
sudo apt-get install xserver-xorg-video-intel
```

followed be a restart did the trick.

I did have to go to System->Preferences->Screen Resolution to select 1440x900, but I mention this just so other folks realize that the updated drivers won't auto-detect the screen resolution for you.

Thanks again!!!!!
-------------------------------------------------------------------------------
Hot Damn it worked here too.

I dual boot on this Dell E1405 and just did a clean install to Feisty from Drapper.  I'd forgotten how I'd gotten 1440*900 to work before and was bummed to not have any option above 1024.

After the apt-get I checked the Screen Resolution options and they hadn't changed.  Rebooted and checked again and the 1440*900 option was there.  Worked GREAT!

BTW - I don't use an external monitor with this laptop.

---

### Post by oregonbob on 2007-09-28
I used "sudo apt-get install xserver-xorg-video-intel" for 7.04 Fiesty and it solved the problem.

Then I upgraded to Gusto 7.10 Beta and it reverted back to 810. If I try ""sudo apt-get install xserver-xorg-video-intel" it errors with 'already installed' message, but it still thinks it is an 810. 810 doesn't have needed resolutions for wide screen (1680X1050 in my case).

Any ideas how to get the 915 driver working on Gusty 7.10?

---

### Post by peabody on 2007-09-28
> **oregonbob said:**
> I used "sudo apt-get install xserver-xorg-video-intel" for 7.04 Fiesty and it solved the problem.

Then I upgraded to Gusto 7.10 Beta and it reverted back to 810. If I try ""sudo apt-get install xserver-xorg-video-intel" it errors with 'already installed' message, but it still thinks it is an 810. 810 doesn't have needed resolutions for wide screen (1680X1050 in my case).

Any ideas how to get the 915 driver working on Gusty 7.10?

Did you try the 915 resolution package?

I have a compaq presario c751nr which has a WXGA screen (1280x800).  I stumbled upon this post before I knew about the 915resolution package, so I used to use the xserver-xorg-video-intel package and was happy as a clam as it got me past my resolution problems of only having 640x480,800x600, and 1024x768 resolutions.  However, I then tried to setup dual and clone setups for the vga out and X would segfault with everything I tried (and yes I changed the driver name in my xorg.conf from i810 to intel).  I then discovered the 915resolution package, so I installed the i810 again (which uninstalled the video-intel driver) and I found that I could get dual and clone setups with the i810 driver with the proper resolution detected on my laptop's LCD (only thing is that dual setups seems to have the wrong aspect ratio on the external, I'm looking into that).

Also, I think there needs to be some clarification on this tread about the use of external monitors.  I get the feeling that some people are booting their laptops with an external plugged in, while other people prefer to plug into an external while their laptop is currently running.  If you prefer to plug your external in first and then power on and use your laptop exclusively with an external monitor, then the video-intel driver seems to be the preference as it properly detects the resolution capabilities of the external monitor that's attached.  However, if your needs are to have a vga out that can be used with a projector for presentations using either a clone setup or a dual setup, then the i810 driver seems to be much better right now.

If anyone has any ideas on the aspect ratio problems I'm having in Xinerama, I'm all ears.

P.S. (Edit) One thing I forgot to mention is that Xv playback does have issues with i810.  Any videos of a resolution greater than or equal to 1024x768 seem to crash video players.  Another reason to use the video-intel for people who need to play videos that big.

---

### Post by tolremeno on 2007-09-28
> **oregonbob said:**
> I used "sudo apt-get install xserver-xorg-video-intel" for 7.04 Fiesty and it solved the problem.

Then I upgraded to Gusto 7.10 Beta and it reverted back to 810. If I try ""sudo apt-get install xserver-xorg-video-intel" it errors with 'already installed' message, but it still thinks it is an 810. 810 doesn't have needed resolutions for wide screen (1680X1050 in my case).

Any ideas how to get the 915 driver working on Gusty 7.10?
I had to use 915resolution on Gutsy to get it to work, although I still haven't gotten it to work on resume (which is how I found this thread).

---

### Post by Mach1US on 2007-10-07
> **ppan76 said:**
> yes the intel drivers will fix the resolution problems...but with the intel drivers I cannot resume from suspend.
With the i810 drivers I am able to do it.
Can anybody do it?

For anybody having problems with 915 diver this worked great for me at least fixing the suspend :
[http://ubuntuforums.org/showthread.php?t=471855](http://ubuntuforums.org/showthread.php?t=471855)

---

