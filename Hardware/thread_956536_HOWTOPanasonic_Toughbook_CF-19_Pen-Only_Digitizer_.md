---
title: "HOWTO:Panasonic Toughbook CF-19 Pen-Only Digitizer Panel Instructions for 8.04"
date: 2008-10-23
forum: Hardware
---

### Post by Rendrago on 2008-10-23
I have a large supply of Panasonic CF-19 Toughbooks with Pen-Only digitizer panels that I was trying to get working with Ubuntu 8.04. It took me two days but I finally got it working.

The most helpful thread was:
[http://ubuntuforums.org/showthread.php?t=870640](http://ubuntuforums.org/showthread.php?t=870640)
(I copied code from this thread for my instructions)

and:
[http://ubuntuforums.org/showthread.php?t=765915](http://ubuntuforums.org/showthread.php?t=765915)


Also:
[https://wiki.edubuntu.org/CF-19](https://wiki.edubuntu.org/CF-19)
[https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom)
[https://help.ubuntu.com/community/WacomTroubleshooting](https://help.ubuntu.com/community/WacomTroubleshooting)
[http://linuxwacom.sourceforge.net/index.php/main](http://linuxwacom.sourceforge.net/index.php/main)

I'm new to Linux and Ubuntu but I'd like to share so no one else has to go through the headache I went through to get these working. What's the best way to share this information? I'd update the Wiki but I'm not sure the best way to go about it. Or is just posting this thread enough?

Here are the the exact steps I took:

```
To install Ubuntu 8.04 on a Panasonic CF-19 Toughbook:

1. From my Windows laptop I use Unetbootin (http://unetbootin.sourceforge.net) to make the Ubuntu 8.04 LTS Desktop Edition ISO (ubuntu-8.04.1-desktop-i386.iso) bootable from a USB memory stick.
2. I boot up the Toughbook from the memory stick and choose the option to Install Ubuntu.
3. Step 1 of 7: I leave the language as English and choose Forward.
4. Step 2 of 7: I leave New York as the Selected City and choose Forward.
5. Step 3 of 7: I leave USA as the Keyboard layout and choose Forward.
6. Step 4 of 7: For the partition, I choose, "Guided - use entire disk" , "SCSI (0,0,0) (sda) - 80.0 GB ATA Hitachi HTS54258" , and then Forward.
7. Step 5 of 7: I enter the name, "Anonymous" which auto-populates the login box with, "anonymous" and the computer name with, "anonymous-laptop". I enter a strong password and choose Forward.
8. Step 6 of 7: There is no step six.
9. Step 7 of 7: I choose Install.
10. After the install I choose Restart Now, remove the memory stick and press enter.

To get the pen-only digitizer panel working:

1. I log into Ubuntu with the "anonymous" login I created during the install.
2. I log into my secure wireless network for internet access.
3. I receive the, "Software updates available" notification.
4. I click on the Update Manager icon and 2 Updates are available.
5. I press the check button and enter my password. The package information is downloaded.
6. There are now 160 updates available.
7. I choose Install Updates (196.5 MB).
8. Once the updates are downloaded and installed, I receive the, "System restart required" message.
9. I close the update manager, click the restart icon in the system tray (two arrows forming a circle), and choose Restart Now.
10. I login again as 'anonymous'.
11. I choose Applications -> Accessories -> Terminal.
12. To download the Linux Wacom drivers I type:

wget http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-5.tar.bz2

13. To make sure we have all the newest/updated packages I type (The password I setup during installation is needed here):

sudo apt-get update

14. To get the other packages we need I type:

sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev

15. I receive a [Y/n] message. I hit Y and Enter.
16. To make absolutely sure we have everything we need I type:

sudo apt-get upgrade

17. To get rid of any older wacom packages I type:

sudo apt-get remove wacom-tools xserver-xorg-input-wacom

18. I receive a [Y/n] message. I hit Y and Enter.
19. To make sure I have the newest kernel headers (or to add them) I type:

sudo apt-get install linux-headers-generic

20. Now back to those drivers we downloaded. To install the drivers I type:

tar xjvf linuxwacom-0.8.1-5.tar.bz2

cd linuxwacom-0.8.1-5

./configure --enable-wacom

make

sudo make install

sudo rmmod wacom

21. You may receive an error after the last command. Ignore the error.
22. To continue to install the drivers, I type:

sudo cp ./src/2.6.24/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

23. Note that the characters before and after uname -r are back ticks, not single quotes. It's the key in the upper left hand corner of a standard keyboard.
24. To continue to install the drivers, I type:

sudo depmod -e

sudo modprobe wacom

25. At this point, the digitized pen will start working but it will be very un-calibrated.
26. To get it working correctly, I type:

gksudo gedit /etc/X11/xorg.conf &

27. This will open up the xorg.conf for editing. Be very careful as a typo here can hose your system.
28. Find the section:

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

29. Change the word 'Touchpad' to 'Pad'.
30. Directly after the section listed above, add the following lines:

Section "InputDevice"
Identifier "stylus"
Driver "wacom"
Option "Type" "stylus"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:1d.0-usb-0:2:1.0-event-mouse"
Option "Button2" "3" # make side-switch a right button
EndSection

Section "InputDevice"
Identifier "touch"
Driver "wacom"
Option "Type" "touch"
Option "USB" "on"
Option "Device" "/dev/input/by-path/pci-0000:00:0b.1-usb-0:2.3:1.1-event-"
EndSection

31. Find the section

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
EndSection

32. Change it to:

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Pad"
	Inputdevice	"stylus"	"SendCoreEvents"
	Inputdevice	"touch"		"SendCoreEvents"
EndSection

33. Note that we changed the word 'Touchpad' to 'Pad' again.
34. Ctrl+S to Save and Ctrl+Q to Quit.
35. Close the terminal and press Ctrl+Alt+Backspace.
36. The digitized pen should work and be calibrated.
```

---

### Post by Rendrago on 2008-12-07
For 8.10:

1.	Install Ubuntu 8.10
2.	Setup Internet Connection
3.	Run Update Manager
4.	cd ./Desktop
5.	wget [http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2](http://prdownloads.sourceforge.net/linuxwacom/linuxwacom-0.8.1-6.tar.bz2)
6.	sudo apt-get update
7.	sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev
8.	sudo apt-get upgrade
9.	sudo apt-get install wacom-tools xserver-xorg-input-wacom
10.	sudo apt-get purge wacom-tools xserver-xorg-input-wacom
11.	sudo apt-get install linux-headers-generic
12.	tar xjvf linuxwacom-0.8.1-5.tar.bz2
13.	cd linuxwacom-0.8.1-5
14.	./configure --enable-wacom --prefix=/usr
15.	make
16.	sudo make install
17.	sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko
18.	REBOOT
20.	sudo depmod -e
21.	sudo modprobe wacom
22.	EDIT xorg.conf

anonymous@anonymous-laptop:~$ cat /etc/X11/xorg.conf

```

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
	InputDevice	"pad"
EndSection

```

23.	Ctrl+Alt+Backspace

---

### Post by Rendrago on 2009-01-08
To get the function keys working:

1. Download this to your Desktop:

[http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2](http://www.da-cha.jp/files/pcc-acpi-0.9.tar.bz2)

Or get it here: [http://www.rendrago.com/linux/pcc-acpi-0.9.tar.bz2](http://www.rendrago.com/linux/pcc-acpi-0.9.tar.bz2)

2. Open up a console and type:

```
cd Desktop/

tar xvf pcc-acpi-0.9.tar.bz2

cd pcc-acpi-0.9/
```

3. Download the file:

[http://www.rendrago.com/linux/pcc_acpi.diff](http://www.rendrago.com/linux/pcc_acpi.diff)

4. Put the file in the folder: /Desktop/pcc-acpi-0.9/
5. Run this:

```
sudo patch pcc_acpi.c pcc_acpi.diff
```

6. You should see: patching file pcc_acpi.c
7. Run this:

```
make

sudo make install

sudo modprobe pcc_acpi
```

8. The function keys should work now (brightness, backlight, volume, etc.). 


I got this information from:

[http://www.da-cha.jp/?q=letsnote](http://www.da-cha.jp/?q=letsnote)

and this page that is currently dead:

[http://lawnjam.com/r4/pcc_acpi.diff](http://lawnjam.com/r4/pcc_acpi.diff)

---

### Post by Favux on 2009-01-09
Hi Rendrago,

Nice HOW TO.  I see you found the gali98 tutorial which is good.  And you've streamlined it, as I have.  I'd like to offer some thoughts regarding your xorg.conf's.

In the 8.04 version you have the xorg.conf set up for a usb tablet.  But the CF-19 is a serial tablet isn't it?  Also it comes in the touch version and the wacom digitizer version, correct?  I'm assuming you have the digitizer version.  In that case you do not need the touch input section or touch in the serverlayout.  You also would not need to change touchpad to pad.

In the 8.10 section you do not need the cursor or pad input sections.  Those are for detachable graphics tablets.  You can remove their entries from serverlayout too.

Does the stylus have an eraser and side button?

Do you need help with rotation?  If so including the output of:
```
xrandr -q --verbose
```
as an uploaded attachment would be helpful.

I hope this is helpful.

---

### Post by Rendrago on 2009-01-09
Hi **Favux**,

Thanks for the reply. I love messing with these things! I'm still VERY new to linux though so bare with me.

> In the 8.04 version you have the xorg.conf set up for a usb tablet. But the CF-19 is a serial tablet isn't it?

The digitizer panel, or Wacom tablet behind the LCD, is considered USB I believe:

```
anonymous@computer:~$ dmesg | grep Wacom
[   17.455869] input: Wacom ISDv4 90 as /devices/pci0000:00/0000:00:1d.0/usb2/2-2/2-2:1.0/input/input7
[   17.477312] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver
```

> Also it comes in the touch version and the wacom digitizer version, correct?

Correct. I have the non-touch. They drive me and my users crazy. The pens do get expensive though.

> I'm assuming you have the digitizer version. In that case you do not need the touch input section or touch in the serverlayout. You also would not need to change touchpad to pad.

The 8.04 post was my first here so I didn't really understand everything I was doing (I still don't). I think I put the touch section in because when I did the dmesg | grep Wacom command in 8.04 and I needed someplace in the xorg.conf to put each /devices/pci outputs (I think there were two in 8.04???). I'm not sure on this one. I'm certainly willing to re-install 8.04 to find out.

I think I changed "touchpad" to "pad" so the actual touchpad below the keyboard would work. But thinking back now I don't think I ever tried leaving it as touchpad. I just took the authors word for it at the time. Again, I'm willing to reload 8.04 if you like.

> In the 8.10 section you do not need the cursor or pad input sections. Those are for detachable graphics tablets. You can remove their entries from serverlayout too.

Can you tell me specifically which sections you think I should remove? I'll back it up and give it a try. Here's the current file:

[http://www.rendrago.com/linux/cf-19_ubuntu810_xorg.conf.txt]("http://www.rendrago.com/linux/cf-19_ubuntu810_xorg.conf.txt")

> Does the stylus have an eraser and side button?

It's got a side button that is currently a right click immediately when it's pressed. I'd like it to act like a mouse where you hold it and then "click". I had this in 8.04 but I can't remember how to get it back.

I don't think I've got an eraser.

> Do you need help with rotation?

YES! I've got six buttons on the front of the unit. Contrast Up, Contrast Down, On Screen Keyboard, Stand By (I think), Screen Rotation, and Lock. The rotation is all I really care about since I got the keyboard fn+F1/fn+F2 backlight/brightness working.

Either the front button or a panel/desktop shortcut. Doesn't really matter.

Here's the xrandr -q:
[http://www.rendrago.com/linux/cf-19_ubuntu810_xrandr-q.txt]("http://www.rendrago.com/linux/cf-19_ubuntu810_xrandr-q.txt")

> I hope this is helpful. 

Like I said; I love messing with these things. I'm willing to try anything. Down the road I'd like to mess with getting encryption unlocked via the SD card slot. I'd also like to have pressure sensitivity in GIMP but that's another thread.

Now if I could just get dual boot linux running with my fake raid Window$ box I'd die a happy man.

:popcorn:

---

### Post by Favux on 2009-01-10
Hi Rendrago,

> I love messing with these things!
I don't blame you, they look cool.

Let me fill you in on some background.  Starting with 8.10 Intepid Ubuntu started switching to HAL (hardware abstraction layer).  This is suppose to replace xorg.conf, and so Intrepid started depopulating it.  HAL allows hotplugging usb devices and other goodness.  The configuration files for HAL are called .fdi files.  It turns out HAL has a few problems.  It should give you stylus support "out of the box".  I suspect it may give side button support too, but I'm not sure.  This could explain the change you noted going from 8.04 to 8.10.  Your stylus may actually be running through HAL not xorg.conf.  You may not need xorg.conf.  Getting the side switch to act the way you want would involve editing the applicable .fdi file.  Now if you had eraser or touch HAL couldn't handle it and so you'd have to revert to xorg.conf.

So one way we could simplify things is start by configuring the xorg.conf in 8.04.  That way there wouldn't be any complications.  Anyway the mouse and touchpad can be handled by HAL, that's why I commented them out.  The keyboard can also be handled by HAL, but there is a problem.  HAL breaks single key key bindings.  So is xev returns a keycode on one of your bezel keys and we bind it for rotation, if you're using HAL for the keyboard, it wouldn't work.  With me so far?  So I'll attach an edited xorg.conf.  Be sure to back yours up, and check it over to make sure I didn't goof.

To calibrate your stylus you need to use the Linux Wacom Projects calibration tool.  In a terminal type "wacomcpl" and a calibration gui pops up.  I don't think it shows "stylus" and the options when you click on it if stylus is running through HAL.  So that may be one way to find out.  This will create a .xinitrc file in the user directory.  We can worry about making available after log in later.  You can also edit it to change your pressure sensitivity.

From your xrandr output it looks like you can use method 1 in my rotation HOW TO.  Hopefully you'll get some output from typing "xev" into a terminal and pressing your bezel keys.  The rotation HOW TO is at:

[http://ubuntuforums.org/showthread.php?t=996830]("http://ubuntuforums.org/showthread.php?t=996830")

Just follow the instructions to get a launcher or to bind a key for rotation.  Follow the thread in a little bit and there is stuff on setting up Gimp.

---

### Post by Rendrago on 2009-01-25
First off, **Favux**, if you're subscribed to this thread, I hope you add some of this to your thread over at:
**_[http://ubuntuforums.org/showthread.php?p=6546012#post6546012](http://ubuntuforums.org/showthread.php?p=6546012#post6546012)_**

It was a big help for me in addition to **_[gali98's original thread]("http://ubuntuforums.org/showthread.php?p=5469447#post5469447")_**.

The grand purpose here is make this process as short as possible.

I'm replying to this thread because the last time I re-installed Ubuntu 8.10 on another one of these Toughbooks, my latest instructions didn't work. So I tried again and learned something new.

What I did:

[LIST=1]
[*]Install using Ubuntu 8.10 i386 Alternate CD (with full disk encryption)
[*]1.System &#8594; Administration &#8594; Update Manager &#8594; Check &#8594; Install Updates
[/LIST]

At this point the xorg.conf is present but completely empty. The touch-pad below the keyboard works as designed. The stylus, front buttons and function keys do not work. Everything else on the Toughbook works pretty much as designed (sound, video, CDMA, etc.)

A search in Synaptic Package Manager for, “wacom” shows xserver-xorg-input-wacom (version 1:0.8.1.4-0ubuntu3) is installed. We also see wacom-tools but it is not installed. We do a few commands from gali98's thread:

```
$ ls -l /dev/input/by-path 
total 0 
lrwxrwxrwx 1 root root 9 2009-01-25 15:59 platform-i8042-serio-0-event-kbd -> ../event1 
lrwxrwxrwx 1 root root 9 2009-01-25 15:59 platform-i8042-serio-4-event-mouse -> ../event7 
lrwxrwxrwx 1 root root 9 2009-01-25 15:59 platform-i8042-serio-4-mouse -> ../mouse1 
lrwxrwxrwx 1 root root 9 2009-01-25 15:59 platform-pcspkr-event-spkr -> ../event6 

```

Appears to be our touch-pad, keyboard and speaker.

```
$ dmesg | grep Wacom

```

This doesn't give us anything as it shouldn't.

I go to [http://linuxwacom.sourceforge.net/](http://linuxwacom.sourceforge.net/) and download version 0.8.2-2 to my Desktop.

Since I'm following a bunch of different tutorials, to be safe lets go over it all again:

```
$ sudo apt-get update
Hit http://us.archive.ubuntu.com intrepid Release.gpg 
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg 
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Hit http://us.archive.ubuntu.com intrepid Release 
Hit http://us.archive.ubuntu.com intrepid-updates Release 
Hit http://us.archive.ubuntu.com intrepid/main Packages 
Hit http://us.archive.ubuntu.com intrepid/restricted Packages 
Hit http://us.archive.ubuntu.com intrepid/main Sources 
Hit http://us.archive.ubuntu.com intrepid/restricted Sources 
Hit http://us.archive.ubuntu.com intrepid/universe Packages 
Hit http://us.archive.ubuntu.com intrepid/universe Sources 
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages 
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources 
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages 
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources 
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources 
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages 
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources 
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages 
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources 
Reading package lists... Done

```

```
$ sudo apt-get install build-essential libx11-dev libxi-dev x11proto-input-dev xserver-xorg-dev tk8.4-dev tcl8.4-dev libncurses5-dev 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following extra packages will be installed: 
  dpkg-dev g++ g++-4.3 libice-dev libpciaccess-dev libpixman-1-dev libpthread-stubs0 libpthread-stubs0-dev libsm-dev 
  libstdc++6-4.3-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxdmcp-dev libxext-dev libxt-dev patch tcl8.4 tk8.4 
  x11proto-core-dev x11proto-fonts-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev 
  x11proto-xext-dev xtrans-dev 
Suggested packages: 
  debian-keyring g++-multilib g++-4.3-multilib gcc-4.3-doc libstdc++6-4.3-dbg libstdc++6-4.3-doc diff-doc tclreadline 
  tcl8.4-doc tk8.4-doc 
The following NEW packages will be installed: 
  build-essential dpkg-dev g++ g++-4.3 libice-dev libncurses5-dev libpciaccess-dev libpixman-1-dev libpthread-stubs0 
  libpthread-stubs0-dev libsm-dev libstdc++6-4.3-dev libx11-dev libxau-dev libxcb-xlib0-dev libxcb1-dev libxdmcp-dev 
  libxext-dev libxi-dev libxt-dev patch tcl8.4 tcl8.4-dev tk8.4 tk8.4-dev x11proto-core-dev x11proto-fonts-dev 
  x11proto-input-dev x11proto-kb-dev x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev 
  xserver-xorg-dev xtrans-dev 
0 upgraded, 35 newly installed, 0 to remove and 0 not upgraded. 
Need to get 15.4MB of archives. 
After this operation, 50.4MB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://us.archive.ubuntu.com intrepid-updates/main x11proto-core-dev 7.0.12-1ubuntu0.1 [90.3kB] 
Get:2 http://us.archive.ubuntu.com intrepid/main libice-dev 2:1.0.4-1 [56.0kB] 
Get:3 http://us.archive.ubuntu.com intrepid/main libsm-dev 2:1.0.3-2 [24.9kB] 
Get:4 http://us.archive.ubuntu.com intrepid/main libxau-dev 1:1.0.3-3 [15.6kB] 
Get:5 http://us.archive.ubuntu.com intrepid/main libxdmcp-dev 1:1.0.2-3 [20.0kB] 
Get:6 http://us.archive.ubuntu.com intrepid/main x11proto-xext-dev 7.0.2-6build1 [42.5kB] 
Get:7 http://us.archive.ubuntu.com intrepid/main libxext-dev 2:1.0.4-1 [84.2kB] 
Get:8 http://us.archive.ubuntu.com intrepid/main libxi-dev 2:1.1.3-2build1 [78.7kB] 
Get:9 http://us.archive.ubuntu.com intrepid/main x11proto-input-dev 1.4.3-2ubuntu6 [11.8kB] 
Get:10 http://us.archive.ubuntu.com intrepid/main x11proto-kb-dev 1.0.3-3ubuntu1 [27.4kB] 
Get:11 http://us.archive.ubuntu.com intrepid/main xtrans-dev 1.2-2 [75.4kB] 
Get:12 http://us.archive.ubuntu.com intrepid/main libpthread-stubs0 0.1-2 [2812B] 
Get:13 http://us.archive.ubuntu.com intrepid/main libpthread-stubs0-dev 0.1-2 [3090B] 
Get:14 http://us.archive.ubuntu.com intrepid/main libxcb1-dev 1.1-1.1 [67.0kB] 
Get:15 http://us.archive.ubuntu.com intrepid/main libxcb-xlib0-dev 1.1-1.1 [14.7kB] 
Get:16 http://us.archive.ubuntu.com intrepid-updates/main libx11-dev 2:1.1.5-2ubuntu1.1 [1706kB] 
Get:17 http://us.archive.ubuntu.com intrepid/main libxt-dev 1:1.0.5-3 [482kB]                                               
Get:18 http://us.archive.ubuntu.com intrepid/main x11proto-fonts-dev 2.0.2-6ubuntu1 [12.5kB]                                
Get:19 http://us.archive.ubuntu.com intrepid/main x11proto-randr-dev 1.2.2-1 [29.5kB]                                       
Get:20 http://us.archive.ubuntu.com intrepid/main x11proto-render-dev 2:0.9.3-2 [7096B]                                     
Get:21 http://us.archive.ubuntu.com intrepid/main x11proto-video-dev 2.2.2-5ubuntu1 [10.2kB]                                
Get:22 http://us.archive.ubuntu.com intrepid/main libstdc++6-4.3-dev 4.3.2-1ubuntu11 [1354kB]                               
Get:23 http://us.archive.ubuntu.com intrepid/main g++-4.3 4.3.2-1ubuntu11 [4128kB]                                          
Get:24 http://us.archive.ubuntu.com intrepid/main g++ 4:4.3.1-1ubuntu2 [1444B]                                              
Get:25 http://us.archive.ubuntu.com intrepid/main patch 2.5.9-5 [100kB]                                                     
Get:26 http://us.archive.ubuntu.com intrepid/main dpkg-dev 1.14.20ubuntu6 [612kB]                                           
Get:27 http://us.archive.ubuntu.com intrepid/main build-essential 11.4 [7172B]                                              
Get:28 http://us.archive.ubuntu.com intrepid/main libncurses5-dev 5.6+20071124-1ubuntu2 [1483kB]                            
Get:29 http://us.archive.ubuntu.com intrepid/main libpixman-1-dev 0.12.0-1 [132kB]                                          
Get:30 http://us.archive.ubuntu.com intrepid/main tcl8.4 8.4.19-2 [1178kB]                                                  
Get:31 http://us.archive.ubuntu.com intrepid/main tcl8.4-dev 8.4.19-2 [799kB]                                               
Get:32 http://us.archive.ubuntu.com intrepid/main tk8.4 8.4.19-1 [1019kB]                                                   
Get:33 http://us.archive.ubuntu.com intrepid/main tk8.4-dev 8.4.19-1 [856kB]                                                
Get:34 http://us.archive.ubuntu.com intrepid/main libpciaccess-dev 0.10.3-1 [25.3kB]                                        
Get:35 http://us.archive.ubuntu.com intrepid/main xserver-xorg-dev 2:1.5.2-2ubuntu3 [838kB]                                 
Fetched 15.4MB in 49s (308kB/s)                                                                                             
Extracting templates from packages: 100% 
Selecting previously deselected package x11proto-core-dev. 
(Reading database ... 115749 files and directories currently installed.) 
Unpacking x11proto-core-dev (from .../x11proto-core-dev_7.0.12-1ubuntu0.1_all.deb) ... 
Selecting previously deselected package libice-dev. 
Unpacking libice-dev (from .../libice-dev_2%3a1.0.4-1_i386.deb) ... 
Selecting previously deselected package libsm-dev. 
Unpacking libsm-dev (from .../libsm-dev_2%3a1.0.3-2_i386.deb) ... 
Selecting previously deselected package libxau-dev. 
Unpacking libxau-dev (from .../libxau-dev_1%3a1.0.3-3_i386.deb) ... 
Selecting previously deselected package libxdmcp-dev. 
Unpacking libxdmcp-dev (from .../libxdmcp-dev_1%3a1.0.2-3_i386.deb) ... 
Selecting previously deselected package x11proto-xext-dev. 
Unpacking x11proto-xext-dev (from .../x11proto-xext-dev_7.0.2-6build1_all.deb) ... 
Selecting previously deselected package libxext-dev. 
Unpacking libxext-dev (from .../libxext-dev_2%3a1.0.4-1_i386.deb) ... 
Selecting previously deselected package libxi-dev. 
Unpacking libxi-dev (from .../libxi-dev_2%3a1.1.3-2build1_i386.deb) ... 
Selecting previously deselected package x11proto-input-dev. 
Unpacking x11proto-input-dev (from .../x11proto-input-dev_1.4.3-2ubuntu6_all.deb) ... 
Selecting previously deselected package x11proto-kb-dev. 
Unpacking x11proto-kb-dev (from .../x11proto-kb-dev_1.0.3-3ubuntu1_all.deb) ... 
Selecting previously deselected package xtrans-dev. 
Unpacking xtrans-dev (from .../xtrans-dev_1.2-2_all.deb) ... 
Selecting previously deselected package libpthread-stubs0. 
Unpacking libpthread-stubs0 (from .../libpthread-stubs0_0.1-2_i386.deb) ... 
Selecting previously deselected package libpthread-stubs0-dev. 
Unpacking libpthread-stubs0-dev (from .../libpthread-stubs0-dev_0.1-2_i386.deb) ... 
Selecting previously deselected package libxcb1-dev. 
Unpacking libxcb1-dev (from .../libxcb1-dev_1.1-1.1_i386.deb) ... 
Selecting previously deselected package libxcb-xlib0-dev. 
Unpacking libxcb-xlib0-dev (from .../libxcb-xlib0-dev_1.1-1.1_i386.deb) ... 
Selecting previously deselected package libx11-dev. 
Unpacking libx11-dev (from .../libx11-dev_2%3a1.1.5-2ubuntu1.1_i386.deb) ... 
Selecting previously deselected package libxt-dev. 
Unpacking libxt-dev (from .../libxt-dev_1%3a1.0.5-3_i386.deb) ... 
Selecting previously deselected package x11proto-fonts-dev. 
Unpacking x11proto-fonts-dev (from .../x11proto-fonts-dev_2.0.2-6ubuntu1_all.deb) ... 
Selecting previously deselected package x11proto-randr-dev. 
Unpacking x11proto-randr-dev (from .../x11proto-randr-dev_1.2.2-1_all.deb) ... 
Selecting previously deselected package x11proto-render-dev. 
Unpacking x11proto-render-dev (from .../x11proto-render-dev_2%3a0.9.3-2_all.deb) ... 
Selecting previously deselected package x11proto-video-dev. 
Unpacking x11proto-video-dev (from .../x11proto-video-dev_2.2.2-5ubuntu1_all.deb) ... 
Selecting previously deselected package libstdc++6-4.3-dev. 
Unpacking libstdc++6-4.3-dev (from .../libstdc++6-4.3-dev_4.3.2-1ubuntu11_i386.deb) ... 
Selecting previously deselected package g++-4.3. 
Unpacking g++-4.3 (from .../g++-4.3_4.3.2-1ubuntu11_i386.deb) ... 
Selecting previously deselected package g++. 
Unpacking g++ (from .../g++_4%3a4.3.1-1ubuntu2_i386.deb) ... 
Selecting previously deselected package patch. 
Unpacking patch (from .../patch_2.5.9-5_i386.deb) ... 
Selecting previously deselected package dpkg-dev. 
Unpacking dpkg-dev (from .../dpkg-dev_1.14.20ubuntu6_all.deb) ... 
Selecting previously deselected package build-essential. 
Unpacking build-essential (from .../build-essential_11.4_i386.deb) ... 
Selecting previously deselected package libncurses5-dev. 
Unpacking libncurses5-dev (from .../libncurses5-dev_5.6+20071124-1ubuntu2_i386.deb) ... 
Selecting previously deselected package libpixman-1-dev. 
Unpacking libpixman-1-dev (from .../libpixman-1-dev_0.12.0-1_i386.deb) ... 
Selecting previously deselected package tcl8.4. 
Unpacking tcl8.4 (from .../tcl8.4_8.4.19-2_i386.deb) ... 
Selecting previously deselected package tcl8.4-dev. 
Unpacking tcl8.4-dev (from .../tcl8.4-dev_8.4.19-2_i386.deb) ... 
Selecting previously deselected package tk8.4. 
Unpacking tk8.4 (from .../tk8.4_8.4.19-1_i386.deb) ... 
Selecting previously deselected package tk8.4-dev. 
Unpacking tk8.4-dev (from .../tk8.4-dev_8.4.19-1_i386.deb) ... 
Selecting previously deselected package libpciaccess-dev. 
Unpacking libpciaccess-dev (from .../libpciaccess-dev_0.10.3-1_i386.deb) ... 
Selecting previously deselected package xserver-xorg-dev. 
Unpacking xserver-xorg-dev (from .../xserver-xorg-dev_2%3a1.5.2-2ubuntu3_i386.deb) ... 
Processing triggers for man-db ... 
Setting up x11proto-core-dev (7.0.12-1ubuntu0.1) ... 
Setting up libice-dev (2:1.0.4-1) ... 
Setting up libsm-dev (2:1.0.3-2) ... 
Setting up libxau-dev (1:1.0.3-3) ... 
Setting up libxdmcp-dev (1:1.0.2-3) ... 
Setting up x11proto-kb-dev (1.0.3-3ubuntu1) ... 
Setting up xtrans-dev (1.2-2) ... 
Setting up libpthread-stubs0 (0.1-2) ... 
Setting up libpthread-stubs0-dev (0.1-2) ... 
Setting up libxcb1-dev (1.1-1.1) ... 
Setting up libxcb-xlib0-dev (1.1-1.1) ... 
Setting up x11proto-fonts-dev (2.0.2-6ubuntu1) ... 
Setting up x11proto-randr-dev (1.2.2-1) ... 
Setting up x11proto-render-dev (2:0.9.3-2) ... 
Setting up x11proto-video-dev (2.2.2-5ubuntu1) ... 
Setting up patch (2.5.9-5) ... 
Setting up dpkg-dev (1.14.20ubuntu6) ... 
Setting up libncurses5-dev (5.6+20071124-1ubuntu2) ... 
Setting up libpixman-1-dev (0.12.0-1) ... 
Setting up tcl8.4 (8.4.19-2) ... 

Setting up tcl8.4-dev (8.4.19-2) ... 
Setting up tk8.4 (8.4.19-1) ... 

Setting up libpciaccess-dev (0.10.3-1) ... 
Setting up libstdc++6-4.3-dev (4.3.2-1ubuntu11) ... 
Setting up x11proto-xext-dev (7.0.2-6build1) ... 
Setting up g++-4.3 (4.3.2-1ubuntu11) ... 
Setting up g++ (4:4.3.1-1ubuntu2) ... 

Setting up build-essential (11.4) ... 
Setting up libxext-dev (2:1.0.4-1) ... 
Setting up libxi-dev (2:1.1.3-2build1) ... 
Setting up x11proto-input-dev (1.4.3-2ubuntu6) ... 
Setting up xserver-xorg-dev (2:1.5.2-2ubuntu3) ... 
Setting up libx11-dev (2:1.1.5-2ubuntu1.1) ... 
Setting up libxt-dev (1:1.0.5-3) ... 
Setting up tk8.4-dev (8.4.19-1) ... 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 

```

```
$ sudo apt-get upgrade 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 

```

```
$ sudo apt-get install wacom-tools xserver-xorg-input-wacom 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
xserver-xorg-input-wacom is already the newest version. 
xserver-xorg-input-wacom set to manually installed. 
The following extra packages will be installed: 
  tcl tk 
The following NEW packages will be installed: 
  tcl tk wacom-tools 
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded. 
Need to get 191kB of archives. 
After this operation, 836kB of additional disk space will be used. 
Do you want to continue [Y/n]? y 
Get:1 http://us.archive.ubuntu.com intrepid/main tcl 8.4.16-2 [4154B] 
Get:2 http://us.archive.ubuntu.com intrepid/main tk 8.4.16-2 [4184B] 
Get:3 http://us.archive.ubuntu.com intrepid/main wacom-tools 1:0.8.1.4-0ubuntu3 [183kB] 
Fetched 191kB in 2s (64.1kB/s)      
Selecting previously deselected package tcl. 
(Reading database ... 119693 files and directories currently installed.) 
Unpacking tcl (from .../archives/tcl_8.4.16-2_all.deb) ... 
Selecting previously deselected package tk. 
Unpacking tk (from .../archives/tk_8.4.16-2_all.deb) ... 
Selecting previously deselected package wacom-tools. 
Unpacking wacom-tools (from .../wacom-tools_1%3a0.8.1.4-0ubuntu3_i386.deb) ... 
Processing triggers for man-db ... 
Setting up tcl (8.4.16-2) ... 

Setting up tk (8.4.16-2) ... 

Setting up wacom-tools (1:0.8.1.4-0ubuntu3) ... 

Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 

```

```
$ sudo apt-get purge wacom-tools xserver-xorg-input-wacom 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
The following packages were automatically installed and are no longer required: 
  tk tcl 
Use 'apt-get autoremove' to remove them. 
The following packages will be REMOVED: 
  wacom-tools* xserver-xorg-input-all* xserver-xorg-input-wacom* 
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded. 
After this operation, 983kB disk space will be freed. 
Do you want to continue [Y/n]? y 
(Reading database ... 119733 files and directories currently installed.) 
Removing wacom-tools ... 
Purging configuration files for wacom-tools ... 
Removing xserver-xorg-input-all ... 
Removing xserver-xorg-input-wacom ... 
Purging configuration files for xserver-xorg-input-wacom ... 
Processing triggers for man-db ... 
Processing triggers for libc6 ... 
ldconfig deferred processing now taking place 
Processing triggers for hal ... 
Regenerating hal fdi cache ... 
Restarting Hardware abstraction layer hald                                                                         [ OK ] 


```

At this point there is no need to get the linux-headers-generic so we then extract.

```
$ tar xjvf linuxwacom-0.8.2-2.tar.bz2 
linuxwacom-0.8.2-2/ 
linuxwacom-0.8.2-2/README 
linuxwacom-0.8.2-2/acinclude.m4 
linuxwacom-0.8.2-2/prebuilt/ 
linuxwacom-0.8.2-2/prebuilt/64/ 
linuxwacom-0.8.2-2/prebuilt/64/wacom_drv.so 
linuxwacom-0.8.2-2/prebuilt/64/.libs/ 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomxi.so.0.0.0 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomcfg.lai 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomcfg.a 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomxi.a 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomxi.lai 
linuxwacom-0.8.2-2/prebuilt/64/.libs/xsetwacom 
linuxwacom-0.8.2-2/prebuilt/64/.libs/libwacomcfg.so.0.0.1 
linuxwacom-0.8.2-2/prebuilt/64/wacomcfg.h 
linuxwacom-0.8.2-2/prebuilt/64/wacomcpl 
linuxwacom-0.8.2-2/prebuilt/64/wacdump 
linuxwacom-0.8.2-2/prebuilt/64/xidump 
linuxwacom-0.8.2-2/prebuilt/64/wacom_drv.o 
linuxwacom-0.8.2-2/prebuilt/64/wacomcpl-exec 
linuxwacom-0.8.2-2/prebuilt/64/xsetwacom 
linuxwacom-0.8.2-2/prebuilt/64/libwacomcfg.la 
linuxwacom-0.8.2-2/prebuilt/64/libwacomxi.la 
linuxwacom-0.8.2-2/prebuilt/64/pkgIndex.tcl 
linuxwacom-0.8.2-2/prebuilt/install 
linuxwacom-0.8.2-2/prebuilt/wacom.4x.gz 
linuxwacom-0.8.2-2/prebuilt/uninstall 
linuxwacom-0.8.2-2/prebuilt/32/ 
linuxwacom-0.8.2-2/prebuilt/32/wacom_drv.so 
linuxwacom-0.8.2-2/prebuilt/32/.libs/ 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomxi.so.0.0.0 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomcfg.lai 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomcfg.a 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomxi.a 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomxi.lai 
linuxwacom-0.8.2-2/prebuilt/32/.libs/xsetwacom 
linuxwacom-0.8.2-2/prebuilt/32/.libs/libwacomcfg.so.0.0.1 
linuxwacom-0.8.2-2/prebuilt/32/wacomcfg.h 
linuxwacom-0.8.2-2/prebuilt/32/wacomcpl 
linuxwacom-0.8.2-2/prebuilt/32/wacdump 
linuxwacom-0.8.2-2/prebuilt/32/xidump 
linuxwacom-0.8.2-2/prebuilt/32/wacom_drv.o 
linuxwacom-0.8.2-2/prebuilt/32/wacomcpl-exec 
linuxwacom-0.8.2-2/prebuilt/32/xsetwacom 
linuxwacom-0.8.2-2/prebuilt/32/libwacomcfg.la 
linuxwacom-0.8.2-2/prebuilt/32/libwacomxi.la 
linuxwacom-0.8.2-2/prebuilt/32/pkgIndex.tcl 
linuxwacom-0.8.2-2/depcomp 
linuxwacom-0.8.2-2/src/ 
linuxwacom-0.8.2-2/src/2.6.8/ 
linuxwacom-0.8.2-2/src/2.6.8/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.8/wacom.c 
linuxwacom-0.8.2-2/src/2.6.8/hid-core.c 
linuxwacom-0.8.2-2/src/2.6.10/ 
linuxwacom-0.8.2-2/src/2.6.10/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.10/wacom.c 
linuxwacom-0.8.2-2/src/2.6.10/hid-core.c 
linuxwacom-0.8.2-2/src/2.6.27/ 
linuxwacom-0.8.2-2/src/2.6.27/wacom.h 
linuxwacom-0.8.2-2/src/2.6.27/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.27/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.26/ 
linuxwacom-0.8.2-2/src/2.6.26/wacom.h 
linuxwacom-0.8.2-2/src/2.6.26/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.26/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.19/ 
linuxwacom-0.8.2-2/src/2.6.19/wacom.h 
linuxwacom-0.8.2-2/src/2.6.19/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.19/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.19/wacom_wac.c 
linuxwacom-0.8.2-2/src/Makefile.am 
linuxwacom-0.8.2-2/src/2.6.14/ 
linuxwacom-0.8.2-2/src/2.6.14/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.14/hid-core.c 
linuxwacom-0.8.2-2/src/xdrv/ 
linuxwacom-0.8.2-2/src/xdrv/xf86Wacom.h 
linuxwacom-0.8.2-2/src/xdrv/Makefile.am 
linuxwacom-0.8.2-2/src/xdrv/xf86Wacom.c 
linuxwacom-0.8.2-2/src/xdrv/wcmConfig.c 
linuxwacom-0.8.2-2/src/xdrv/wcmCommon.c 
linuxwacom-0.8.2-2/src/xdrv/wcmFilter.c 
linuxwacom-0.8.2-2/src/xdrv/Makefile.in 
linuxwacom-0.8.2-2/src/xdrv/wcmUSB.c 
linuxwacom-0.8.2-2/src/xdrv/wcmSerial.h 
linuxwacom-0.8.2-2/src/xdrv/wcmSerial.c 
linuxwacom-0.8.2-2/src/xdrv/wcmISDV4.c 
linuxwacom-0.8.2-2/src/xdrv/wcmXCommand.c 
linuxwacom-0.8.2-2/src/xdrv/wcmFilter.h 
linuxwacom-0.8.2-2/src/xdrv/wcmCompat.c 
linuxwacom-0.8.2-2/src/xdrv/xf86WacomDefs.h 
linuxwacom-0.8.2-2/src/2.6.11/ 
linuxwacom-0.8.2-2/src/2.6.11/wacom.h 
linuxwacom-0.8.2-2/src/2.6.11/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.11/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.11/hid-core.c 
linuxwacom-0.8.2-2/src/wacom.4x 
linuxwacom-0.8.2-2/src/include/ 
linuxwacom-0.8.2-2/src/include/kernel-config.h.in 
linuxwacom-0.8.2-2/src/include/util-config.h.in 
linuxwacom-0.8.2-2/src/include/Xwacom.h 
linuxwacom-0.8.2-2/src/include/xdrv-config.h.in 
linuxwacom-0.8.2-2/src/2.4/ 
linuxwacom-0.8.2-2/src/2.4/usbmouse.c 
linuxwacom-0.8.2-2/src/2.4/hiddev.c 
linuxwacom-0.8.2-2/src/2.4/hid-input.c 
linuxwacom-0.8.2-2/src/2.4/Makefile.am 
linuxwacom-0.8.2-2/src/2.4/evdev.c 
linuxwacom-0.8.2-2/src/2.4/Makefile.in 
linuxwacom-0.8.2-2/src/2.4/wacom.c 
linuxwacom-0.8.2-2/src/2.4/mousedev.c 
linuxwacom-0.8.2-2/src/2.4/input.c 
linuxwacom-0.8.2-2/src/2.4/hid-core.c 
linuxwacom-0.8.2-2/src/2.6.15/ 
linuxwacom-0.8.2-2/src/2.6.15/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.15/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.15/hid-core.c 
linuxwacom-0.8.2-2/src/2.6.9/ 
linuxwacom-0.8.2-2/src/2.6.9/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.9/wacom.c 
linuxwacom-0.8.2-2/src/2.6.9/hid-core.c 
linuxwacom-0.8.2-2/src/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.18/ 
linuxwacom-0.8.2-2/src/2.6.18/wacom.h 
linuxwacom-0.8.2-2/src/2.6.18/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.22/ 
linuxwacom-0.8.2-2/src/2.6.22/wacom_wac.h 
linuxwacom-0.8.2-2/src/2.6.22/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.22/Makefile.in 
linuxwacom-0.8.2-2/src/2.4.22/ 
linuxwacom-0.8.2-2/src/2.4.22/Makefile.am 
linuxwacom-0.8.2-2/src/2.4.22/evdev.c 
linuxwacom-0.8.2-2/src/2.4.22/Makefile.in 
linuxwacom-0.8.2-2/src/2.4.22/wacom.c 
linuxwacom-0.8.2-2/src/2.4.22/mousedev.c 
linuxwacom-0.8.2-2/src/2.4.22/hid-core.c 
linuxwacom-0.8.2-2/src/wacomxi/ 
linuxwacom-0.8.2-2/src/wacomxi/wacomcpl 
linuxwacom-0.8.2-2/src/wacomxi/wacomcpl.in 
linuxwacom-0.8.2-2/src/wacomxi/wacomxi.h 
linuxwacom-0.8.2-2/src/wacomxi/Makefile.am 
linuxwacom-0.8.2-2/src/wacomxi/wacomxi.c 
linuxwacom-0.8.2-2/src/wacomxi/Makefile.in 
linuxwacom-0.8.2-2/src/wacomxi/wacomcpl-exec 
linuxwacom-0.8.2-2/src/wacomxi/pkgIndex.tcl 
linuxwacom-0.8.2-2/src/2.4.30x86-64/ 
linuxwacom-0.8.2-2/src/2.4.30x86-64/usbmouse.c 
linuxwacom-0.8.2-2/src/2.4.30x86-64/evdev.c 
linuxwacom-0.8.2-2/src/2.4.30x86-64/wacom.c 
linuxwacom-0.8.2-2/src/2.4.30x86-64/mousedev.c 
linuxwacom-0.8.2-2/src/2.4.30x86-64/hid-core.c 
linuxwacom-0.8.2-2/src/2.6.24/ 
linuxwacom-0.8.2-2/src/2.6.24/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.24/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.13/ 
linuxwacom-0.8.2-2/src/2.6.13/wacom.h 
linuxwacom-0.8.2-2/src/2.6.13/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.13/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.13/hid-core.c 
linuxwacom-0.8.2-2/src/util/ 
linuxwacom-0.8.2-2/src/util/wacserial.c 
linuxwacom-0.8.2-2/src/util/wacdump.c 
linuxwacom-0.8.2-2/src/util/xsetwacom.c 
linuxwacom-0.8.2-2/src/util/wacomcfg.c 
linuxwacom-0.8.2-2/src/util/wacomcfg.h 
linuxwacom-0.8.2-2/src/util/Makefile.am 
linuxwacom-0.8.2-2/src/util/xidump.c 
linuxwacom-0.8.2-2/src/util/wacscrn.c 
linuxwacom-0.8.2-2/src/util/wcmAction.h 
linuxwacom-0.8.2-2/src/util/Makefile.in 
linuxwacom-0.8.2-2/src/util/wacusb.c 
linuxwacom-0.8.2-2/src/util/wactablet.h 
linuxwacom-0.8.2-2/src/util/wacusb.h 
linuxwacom-0.8.2-2/src/util/wcmAction.c 
linuxwacom-0.8.2-2/src/util/wacscrn.h 
linuxwacom-0.8.2-2/src/util/wacserial.h 
linuxwacom-0.8.2-2/src/util/wactablet.c 
linuxwacom-0.8.2-2/src/2.6.16/ 
linuxwacom-0.8.2-2/src/2.6.16/wacom.h 
linuxwacom-0.8.2-2/src/2.6.16/wacom_wac.h 
linuxwacom-0.8.2-2/src/2.6.16/wacom_sys.c 
linuxwacom-0.8.2-2/src/2.6.16/Makefile.in 
linuxwacom-0.8.2-2/src/2.6.16/wacom_wac.c 
linuxwacom-0.8.2-2/src/2.6.16/hid-core.c 
linuxwacom-0.8.2-2/mkxincludes.in 
linuxwacom-0.8.2-2/install-sh 
linuxwacom-0.8.2-2/config.guess 
linuxwacom-0.8.2-2/Makefile.am 
linuxwacom-0.8.2-2/autom4te.cache/ 
linuxwacom-0.8.2-2/autom4te.cache/output.1 
linuxwacom-0.8.2-2/autom4te.cache/output.0 
linuxwacom-0.8.2-2/autom4te.cache/traces.1 
linuxwacom-0.8.2-2/autom4te.cache/traces.0 
linuxwacom-0.8.2-2/autom4te.cache/requests 
linuxwacom-0.8.2-2/ltmain.sh 
linuxwacom-0.8.2-2/aclocal.m4 
linuxwacom-0.8.2-2/GPL 
linuxwacom-0.8.2-2/ChangeLog 
linuxwacom-0.8.2-2/LGPL 
linuxwacom-0.8.2-2/configure.in 
linuxwacom-0.8.2-2/Makefile.in 
linuxwacom-0.8.2-2/missing 
linuxwacom-0.8.2-2/config.sub 
linuxwacom-0.8.2-2/AUTHORS 
linuxwacom-0.8.2-2/bootstrap 
linuxwacom-0.8.2-2/NEWS 
linuxwacom-0.8.2-2/configure 

```

We CD to the new directory and run configure:

```
$ ./configure --enable-wacom --prefix=/usr 
checking for a BSD-compatible install... /usr/bin/install -c 
checking whether build environment is sane... yes 
checking for gawk... no 
checking for mawk... mawk 
checking whether make sets $(MAKE)... yes 
checking whether to enable maintainer-specific portions of Makefiles... no 
checking for gcc... gcc 
checking for C compiler default output file name... a.out 
checking whether the C compiler works... yes 
checking whether we are cross compiling... no 
checking for suffix of executables... 
checking for suffix of object files... o 
checking whether we are using the GNU C compiler... yes 
checking whether gcc accepts -g... yes 
checking for gcc option to accept ANSI C... none needed 
checking for style of include used by make... GNU 
checking dependency style of gcc... gcc3 
checking for gawk... (cached) mawk 
checking build system type... i686-pc-linux-gnu 
checking host system type... i686-pc-linux-gnu 
checking for a sed that does not truncate output... /bin/sed 
checking for egrep... grep -E 
checking for ld used by gcc... /usr/bin/ld 
checking if the linker (/usr/bin/ld) is GNU ld... yes 
checking for /usr/bin/ld option to reload object files... -r 
checking for BSD-compatible nm... /usr/bin/nm -B 
checking whether ln -s works... yes 
checking how to recognise dependent libraries... pass_all 
checking how to run the C preprocessor... gcc -E 
checking for ANSI C header files... yes 
checking for sys/types.h... yes 
checking for sys/stat.h... yes 
checking for stdlib.h... yes 
checking for string.h... yes 
checking for memory.h... yes 
checking for strings.h... yes 
checking for inttypes.h... yes 
checking for stdint.h... yes 
checking for unistd.h... yes 
checking dlfcn.h usability... yes 
checking dlfcn.h presence... yes 
checking for dlfcn.h... yes 
checking for g++... g++ 
checking whether we are using the GNU C++ compiler... yes 
checking whether g++ accepts -g... yes 
checking dependency style of g++... gcc3 
checking how to run the C++ preprocessor... g++ -E 
checking for g77... no 
checking for f77... no 
checking for xlf... no 
checking for frt... no 
checking for pgf77... no 
checking for fort77... no 
checking for fl32... no 
checking for af77... no 
checking for f90... no 
checking for xlf90... no 
checking for pgf90... no 
checking for epcf90... no 
checking for f95... no 
checking for fort... no 
checking for xlf95... no 
checking for ifc... no 
checking for efc... no 
checking for pgf95... no 
checking for lf95... no 
checking for gfortran... no 
checking whether we are using the GNU Fortran 77 compiler... no 
checking whether  accepts -g... no 
checking the maximum length of command line arguments... 32768 
checking command to parse /usr/bin/nm -B output from gcc object... ok 
checking for objdir... .libs 
checking for ar... ar 
checking for ranlib... ranlib 
checking for strip... strip 
checking if gcc supports -fno-rtti -fno-exceptions... no 
checking for gcc option to produce PIC... -fPIC 
checking if gcc PIC flag -fPIC works... yes 
checking if gcc static flag -static works... yes 
checking if gcc supports -c -o file.o... yes 
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes 
checking whether -lc should be explicitly linked in... no 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
checking whether stripping libraries is possible... yes 
checking if libtool supports shared libraries... yes 
checking whether to build shared libraries... yes 
checking whether to build static libraries... yes 
configure: creating libtool 
appending configuration tag "CXX" to libtool 
checking for ld used by g++... /usr/bin/ld 
checking if the linker (/usr/bin/ld) is GNU ld... yes 
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes 
checking for g++ option to produce PIC... -fPIC 
checking if g++ PIC flag -fPIC works... yes 
checking if g++ static flag -static works... yes 
checking if g++ supports -c -o file.o... yes 
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes 
checking dynamic linker characteristics... GNU/Linux ld.so 
checking how to hardcode library paths into programs... immediate 
appending configuration tag "F77" to libtool 
checking for pkg-config... /usr/bin/pkg-config 
checking pkg-config is at least version 0.9.0... yes 
checking for arch type... i486-linux-gnu 
checking for kernel type... Linux 
checking for linux-based kernel... yes 
checking for kernel source/headers... /lib/modules/2.6.27-9-generic/build 
checking kernel version... 2.6.27-9-generic 
checking for kernel module support... yes 
checking for Xlib... yes 
checking for XSERVER... yes 
checking for xserver libc-wrapper header-files... no 
checking if scaling tablet to screen size is needed... no 
checking if Uninit is called... yes 
checking if Xorg is version 1.6 or later... no 
checking if Xorg SDK defines IsXExtensionPointer... yes 
checking if Xorg SDK defines dixScreenOrigins... yes 
checking XInput extension version... >= 2.0 
checking for lib xf86config... checking for X... libraries , headers 
checking for gethostbyname... yes 
checking for connect... yes 
checking for remove... yes 
checking for shmat... yes 
checking for IceConnectionNumber in -lICE... yes 
checking for tclsh... /usr/bin/tclsh 
checking for tcl version... 8.4 
checking for tcl header files... found, /usr/include/tcl8.4 
checking for tk header files... found, /usr/include/tcl8.4 
checking ncurses.h usability... yes 
checking ncurses.h presence... yes 
checking for ncurses.h... yes 
checking if libwacomcfg should/can be built... yes 
checking if libwacomxi should/can be built... yes 
checking if wacdump should/can be built... yes 
checking if xidump should/can be built... yes 
checking if xsetwacom should be built... yes 
checking for Wacom X driver module path... /usr/lib/xorg/modules/input 
checking for dynamic driver loading support... yes 
checking if wacom_drv.{o,so} should be compiled... yes 
checking if gcc accepts -fno-merge-constants... yes 
checking if gcc accepts -fno-stack-protector... yes 

configure: creating ./config.status 
config.status: creating Makefile 
config.status: creating mkxincludes 
config.status: creating src/Makefile 
config.status: creating src/util/Makefile 
config.status: creating src/xdrv/Makefile 
config.status: creating src/2.4/Makefile 
config.status: creating src/2.4.22/Makefile 
config.status: creating src/2.6.8/Makefile 
config.status: creating src/2.6.9/Makefile 
config.status: creating src/2.6.10/Makefile 
config.status: creating src/2.6.11/Makefile 
config.status: creating src/2.6.13/Makefile 
config.status: creating src/2.6.14/Makefile 
config.status: creating src/2.6.15/Makefile 
config.status: creating src/2.6.16/Makefile 
config.status: creating src/2.6.18/Makefile 
config.status: creating src/2.6.19/Makefile 
config.status: creating src/2.6.22/Makefile 
config.status: creating src/2.6.24/Makefile 
config.status: creating src/2.6.26/Makefile 
config.status: creating src/2.6.27/Makefile 
config.status: creating src/wacomxi/Makefile 
config.status: creating src/wacomxi/wacomcpl 
config.status: creating src/include/xdrv-config.h 
config.status: creating src/include/kernel-config.h 
config.status: creating src/include/util-config.h 
config.status: executing depfiles commands 

---------------------------------------- 
  BUILD ENVIRONMENT: 
       architecture - i486-linux-gnu 
       linux kernel - yes 2.6.27 
  module versioning - no 
      kernel source - yes /lib/modules/2.6.27-9-generic/build 
     XFree86 source - no 
           Xorg SDK - yes /usr/include/xorg 
          XSERVER64 - no 
           dlloader - yes 
               XLib - yes /usr/lib 
         xf86config - no 
                TCL - yes /usr/include/tcl8.4 
                 TK - yes /usr/include/tcl8.4 
            ncurses - yes 

  BUILD OPTIONS: 
            wacom.o - yes 
            wacdump - yes 
             xidump - yes 
        libwacomcfg - yes 
         libwacomxi - yes 
          xsetwacom - yes 
              hid.o - no 
         usbmouse.o - no 
            evdev.o - no 
         mousedev.o - no 
            input.o - no 
       wacom_drv.so - yes /usr/lib/xorg/modules/input 
        wacom_drv.o - no 
  wacom*_drv quirks - Uninit-called IsXExtensionPointer key-events dixScreenOrigins 
---------------------------------------- 

```

Now we run make:

```
$ make 
Making all in src 
make[1]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
Making all in . 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
rm -f wacom.4x.gz 
gzip -9c < ./wacom.4x > wacom.4x.gz 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
Making all in wacomxi 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -g -O2 -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF ".deps/wacomxi.Tpo" -c -o wacomxi.lo wacomxi.c; \ 
	then mv -f ".deps/wacomxi.Tpo" ".deps/wacomxi.Plo"; else rm -f ".deps/wacomxi.Tpo"; exit 1; fi 
mkdir .libs 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c  -fPIC -DPIC -o .libs/wacomxi.o 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -g -O2 -I/usr/include/tcl8.4 -MT wacomxi.lo -MD -MP -MF .deps/wacomxi.Tpo -c wacomxi.c -o wacomxi.o >/dev/null 2>&1 
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -g -O2 -I/usr/include/tcl8.4   -o libwacomxi.la -rpath /usr/lib/TkXInput -no-undefined wacomxi.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomxi.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomxi.so.0 -o .libs/libwacomxi.so.0.0.0 
(cd .libs && rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0) 
(cd .libs && rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so) 
ar cru .libs/libwacomxi.a  wacomxi.o 
ranlib .libs/libwacomxi.a 
creating libwacomxi.la 
(cd .libs && rm -f libwacomxi.la && ln -s ../libwacomxi.la libwacomxi.la) 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 
Making all in util 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF ".deps/wacomcfg.Tpo" -c -o wacomcfg.lo wacomcfg.c; \ 
	then mv -f ".deps/wacomcfg.Tpo" ".deps/wacomcfg.Plo"; else rm -f ".deps/wacomcfg.Tpo"; exit 1; fi 
mkdir .libs 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c  -fPIC -DPIC -o .libs/wacomcfg.o 
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include -Wall -pedantic -I/usr/include/xorg -g -O2 -I/usr/include/tcl8.4 -MT wacomcfg.lo -MD -MP -MF .deps/wacomcfg.Tpo -c wacomcfg.c -o wacomcfg.o >/dev/null 2>&1 
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4   -o libwacomcfg.la -rpath /usr/lib -no-undefined -version-info 0:1:0 wacomcfg.lo -L/usr/lib -lX11 -lXi 
gcc -shared  .libs/wacomcfg.o  -L/usr/lib -lX11 -lXi  -Wl,-soname -Wl,libwacomcfg.so.0 -o .libs/libwacomcfg.so.0.0.1 
(cd .libs && rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0) 
(cd .libs && rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so) 
ar cru .libs/libwacomcfg.a  wacomcfg.o 
ranlib .libs/libwacomcfg.a 
creating libwacomcfg.la 
(cd .libs && rm -f libwacomcfg.la && ln -s ../libwacomcfg.la libwacomcfg.la) 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wacdump.o -MD -MP -MF ".deps/wacdump.Tpo" -c -o wacdump.o wacdump.c; \ 
	then mv -f ".deps/wacdump.Tpo" ".deps/wacdump.Po"; else rm -f ".deps/wacdump.Tpo"; exit 1; fi 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wacscrn.o -MD -MP -MF ".deps/wacscrn.Tpo" -c -o wacscrn.o wacscrn.c; \ 
	then mv -f ".deps/wacscrn.Tpo" ".deps/wacscrn.Po"; else rm -f ".deps/wacscrn.Tpo"; exit 1; fi 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wactablet.o -MD -MP -MF ".deps/wactablet.Tpo" -c -o wactablet.o wactablet.c; \ 
	then mv -f ".deps/wactablet.Tpo" ".deps/wactablet.Po"; else rm -f ".deps/wactablet.Tpo"; exit 1; fi 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wacserial.o -MD -MP -MF ".deps/wacserial.Tpo" -c -o wacserial.o wacserial.c; \ 
	then mv -f ".deps/wacserial.Tpo" ".deps/wacserial.Po"; else rm -f ".deps/wacserial.Tpo"; exit 1; fi 
wacserial.c: In function ‘WacomFlush’: 
wacserial.c:1345: warning: ignoring return value of ‘read’, declared with attribute warn_unused_result 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wacusb.o -MD -MP -MF ".deps/wacusb.Tpo" -c -o wacusb.o wacusb.c; \ 
	then mv -f ".deps/wacusb.Tpo" ".deps/wacusb.Po"; else rm -f ".deps/wacusb.Tpo"; exit 1; fi 
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4   -o wacdump  wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -I/usr/include/tcl8.4 -o wacdump wacdump.o wacscrn.o wactablet.o wacserial.o wacusb.o  -lncurses 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT xidump.o -MD -MP -MF ".deps/xidump.Tpo" -c -o xidump.o xidump.c; \ 
	then mv -f ".deps/xidump.Tpo" ".deps/xidump.Po"; else rm -f ".deps/xidump.Tpo"; exit 1; fi 
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4   -o xidump -L/usr/lib -lX11 -lXi -lm xidump.o wacscrn.o -lncurses 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -I/usr/include/tcl8.4 -o xidump xidump.o wacscrn.o  -L/usr/lib -lX11 -lXi -lm -lncurses 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT xsetwacom.o -MD -MP -MF ".deps/xsetwacom.Tpo" -c -o xsetwacom.o xsetwacom.c; \ 
	then mv -f ".deps/xsetwacom.Tpo" ".deps/xsetwacom.Po"; else rm -f ".deps/xsetwacom.Tpo"; exit 1; fi 
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src/include -I../../src/include -I../../src/include    -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4 -MT wcmAction.o -MD -MP -MF ".deps/wcmAction.Tpo" -c -o wcmAction.o wcmAction.c; \ 
	then mv -f ".deps/wcmAction.Tpo" ".deps/wcmAction.Po"; else rm -f ".deps/wcmAction.Tpo"; exit 1; fi 
/bin/bash ../../libtool --tag=CC --mode=link gcc -Wall -pedantic -I/usr/include/xorg  -g -O2 -I/usr/include/tcl8.4   -o xsetwacom  xsetwacom.o wcmAction.o libwacomcfg.la 
gcc -Wall -pedantic -I/usr/include/xorg -g -O2 -I/usr/include/tcl8.4 -o .libs/xsetwacom xsetwacom.o wcmAction.o  ./.libs/libwacomcfg.so -L/usr/lib -lX11 -lXi 
creating xsetwacom 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
Making all in xdrv 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
gcc -MM -g -O2 -I/usr/include/tcl8.4  -I../include -I/usr/include/xorg  ./xf86Wacom.c ./wcmSerial.c ./wcmUSB.c ./wcmISDV4.c ./wcmXCommand.c ./wcmCommon.c ./wcmCompat.c ./wcmConfig.c ./wcmFilter.c > .depend 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o xf86Wacom.o -c ./xf86Wacom.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmSerial.o -c ./wcmSerial.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmUSB.o -c ./wcmUSB.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmISDV4.o -c ./wcmISDV4.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmXCommand.o -c ./wcmXCommand.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmCommon.o -c ./wcmCommon.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmCompat.o -c ./wcmCompat.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmConfig.o -c ./wcmConfig.c 
gcc -g -O2 -I/usr/include/tcl8.4  -fPIC -pipe -std=c99 \ 
		-pedantic -Wall -Wpointer-arith -fno-merge-constants \ 
		-fno-stack-protector -I. -I../include -I/usr/include/xorg  \ 
		 -I/usr/include/xorg -I/usr/include/pixman-1   \ 
		-o wcmFilter.o -c ./wcmFilter.c 
gcc -shared -nostdlib -o wacom_drv.so xf86Wacom.o wcmSerial.o wcmUSB.o wcmISDV4.o wcmXCommand.o wcmCommon.o wcmCompat.o wcmConfig.o wcmFilter.o -Bstatic -lgcc 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
Making all in 2.6.27 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27' 
cp -f ../2.6.19/wacom_wac.c . 
cp -f ../2.6.22/wacom_wac.h . 
    Building linuxwacom drivers for 2.6 kernel. 
***Note: Drivers not enabled as modules in your kernel config but requested through configure are NOT built 
make -C /lib/modules/2.6.27-9-generic/build M=/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27 
make[3]: Entering directory `/usr/src/linux-headers-2.6.27-9-generic' 
  LD      /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/built-in.o 
  CC [M]  /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/wacom_wac.o 
  CC [M]  /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/wacom_sys.o 
  LD [M]  /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/wacom.o 
  Building modules, stage 2. 
  MODPOST 1 modules 
  CC      /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/wacom.mod.o 
  LD [M]  /home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27/wacom.ko 
make[3]: Leaving directory `/usr/src/linux-headers-2.6.27-9-generic' 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27' 
make[1]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
make[1]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 
make[1]: Nothing to be done for `all-am'. 
make[1]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 

```

```
$ sudo make install 
Making install in src 
make[1]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
Making install in . 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
make[3]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
make[3]: Nothing to be done for `install-exec-am'. 
test -z "/usr/man/man4" || mkdir -p -- "/usr/man/man4" 
 /usr/bin/install -c -m 644 'wacom.4x.gz' '/usr/man/man4/wacom.4x.gz' 
make[3]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
Making install in wacomxi 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 
make[3]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 
make[3]: Nothing to be done for `install-exec-am'. 
test -z "/usr/bin" || mkdir -p -- "/usr/bin" 
 /usr/bin/install -c 'wacomcpl' '/usr/bin/wacomcpl' 
 /usr/bin/install -c 'wacomcpl-exec' '/usr/bin/wacomcpl-exec' 
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput" 
 /usr/bin/install -c -m 644 'pkgIndex.tcl' '/usr/lib/TkXInput/pkgIndex.tcl' 
test -z "/usr/lib/TkXInput" || mkdir -p -- "/usr/lib/TkXInput" 
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomxi.la' '/usr/lib/TkXInput/libwacomxi.la' 
/usr/bin/install -c .libs/libwacomxi.so.0.0.0 /usr/lib/TkXInput/libwacomxi.so.0.0.0 
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so.0 || { rm -f libwacomxi.so.0 && ln -s libwacomxi.so.0.0.0 libwacomxi.so.0; }; }) 
(cd /usr/lib/TkXInput && { ln -s -f libwacomxi.so.0.0.0 libwacomxi.so || { rm -f libwacomxi.so && ln -s libwacomxi.so.0.0.0 libwacomxi.so; }; }) 
/usr/bin/install -c .libs/libwacomxi.lai /usr/lib/TkXInput/libwacomxi.la 
/usr/bin/install -c .libs/libwacomxi.a /usr/lib/TkXInput/libwacomxi.a 
chmod 644 /usr/lib/TkXInput/libwacomxi.a 
ranlib /usr/lib/TkXInput/libwacomxi.a 
PATH="$PATH:/sbin" ldconfig -n /usr/lib/TkXInput 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/lib/TkXInput 

If you ever happen to want to link against installed libraries 
in a given directory, LIBDIR, you must either use libtool, and 
specify the full pathname of the library, or use the `-LLIBDIR' 
flag during linking and do at least one of the following: 
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable 
     during execution 
   - add LIBDIR to the `LD_RUN_PATH' environment variable 
     during linking 
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag 
   - have your system administrator add LIBDIR to `/etc/ld.so.conf' 

See any operating system documentation about shared libraries for 
more information, such as the ld(1) and ld.so(8) manual pages. 
---------------------------------------------------------------------- 
make[3]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/wacomxi' 

Making install in util 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
make[3]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
test -z "/usr/lib" || mkdir -p -- "/usr/lib" 
 /bin/bash ../../libtool --mode=install /usr/bin/install -c  'libwacomcfg.la' '/usr/lib/libwacomcfg.la' 
/usr/bin/install -c .libs/libwacomcfg.so.0.0.1 /usr/lib/libwacomcfg.so.0.0.1 
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so.0 || { rm -f libwacomcfg.so.0 && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so.0; }; }) 
(cd /usr/lib && { ln -s -f libwacomcfg.so.0.0.1 libwacomcfg.so || { rm -f libwacomcfg.so && ln -s libwacomcfg.so.0.0.1 libwacomcfg.so; }; }) 
/usr/bin/install -c .libs/libwacomcfg.lai /usr/lib/libwacomcfg.la 
/usr/bin/install -c .libs/libwacomcfg.a /usr/lib/libwacomcfg.a 
chmod 644 /usr/lib/libwacomcfg.a 
ranlib /usr/lib/libwacomcfg.a 
PATH="$PATH:/sbin" ldconfig -n /usr/lib 
---------------------------------------------------------------------- 
Libraries have been installed in: 
   /usr/lib 

If you ever happen to want to link against installed libraries 
in a given directory, LIBDIR, you must either use libtool, and 
specify the full pathname of the library, or use the `-LLIBDIR' 
flag during linking and do at least one of the following: 
   - add LIBDIR to the `LD_LIBRARY_PATH' environment variable 
     during execution 
   - add LIBDIR to the `LD_RUN_PATH' environment variable 
     during linking 
   - use the `-Wl,--rpath -Wl,LIBDIR' linker flag 
   - have your system administrator add LIBDIR to `/etc/ld.so.conf' 

See any operating system documentation about shared libraries for 
more information, such as the ld(1) and ld.so(8) manual pages. 
---------------------------------------------------------------------- 
test -z "/usr/bin" || mkdir -p -- "/usr/bin" 
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'wacdump' '/usr/bin/wacdump' 
/usr/bin/install -c wacdump /usr/bin/wacdump 
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xidump' '/usr/bin/xidump' 
/usr/bin/install -c xidump /usr/bin/xidump 
  /bin/bash ../../libtool --mode=install /usr/bin/install -c 'xsetwacom' '/usr/bin/xsetwacom' 
/usr/bin/install -c .libs/xsetwacom /usr/bin/xsetwacom 
test -z "/usr/include/wacomcfg" || mkdir -p -- "/usr/include/wacomcfg" 
 /usr/bin/install -c -m 644 'wacomcfg.h' '/usr/include/wacomcfg/wacomcfg.h' 
make[3]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/util' 
Making install in xdrv 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
make[3]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
make[3]: Nothing to be done for `install-exec-am'. 
test -z "/usr/lib/xorg/modules/input" || mkdir -p -- "/usr/lib/xorg/modules/input" 
 /usr/bin/install -c -m 644 'wacom_drv.so' '/usr/lib/xorg/modules/input/wacom_drv.so' 
make[3]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/xdrv' 
Making install in 2.6.27 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27' 
make[2]: Nothing to be done for `install'. 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src/2.6.27' 
make[1]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2/src' 
make[1]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 
make[2]: Entering directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 
make[2]: Nothing to be done for `install-exec-am'. 
make[2]: Nothing to be done for `install-data-am'. 
make[2]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 
make[1]: Leaving directory `/home/anonymous/Desktop/linuxwacom-0.8.2-2' 

```

Then we copy our new driver over to the appropriate folder:

```
sudo cp ./src/2.6.27/wacom.ko /lib/modules/`uname -r`/kernel/drivers/input/tablet/wacom.ko

```

At this point, per gali98, we reboot. Continuing:

```
$ sudo depmod -e

$ sudo modprobe wacom

```

At this point everything should still not work and we still have an empty xorg.conf.

**[SIZE="5"]This is the part that I learned today![/SIZE]**

I run the commands to see how linux sees the digitizer panel (tablet):

```
$ dmesg | grep Wacom
[   48.902519] input: Wacom ISDv4 90 as /devices/pci0000:00/0000:00:1d.0/usb1/1-2/1-2:1.0/input/input6
[   48.932422] wacom: v1.49:USB Wacom Graphire and Wacom Intuos tablet driver

```

Be very careful as something causes these values to sometimes change. I haven't figured that one out yet.

```
$ ls -l /dev/input/by-path/
total 0
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 pci-0000:00:1d.0-usb-0:2:1.0-event-mouse -> ../event6
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 pci-0000:00:1d.0-usb-0:2:1.0-mouse -> ../mouse1
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 platform-i8042-serio-0-event-kbd -> ../event1
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 platform-i8042-serio-4-event-mouse -> ../event8
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 platform-i8042-serio-4-mouse -> ../mouse2
lrwxrwxrwx 1 root root 9 2009-01-25 19:19 platform-pcspkr-event-spkr -> ../event7

```

Now I know that /dev/input/ is where my input devices are and that /by-path/ is just showing me them sorted by path so maybe I can use the events in my xorg.conf instead of the whole pci path. 

So after quite a bit of trial and error, I came up with:

```
Section "Device" 
	Identifier	"Configured Video Device" 
EndSection 

Section "Monitor" 
	Identifier	"Configured Monitor" 
EndSection 

Section "Screen" 
	Identifier	"Default Screen" 
	Monitor		"Configured Monitor" 
	Device		"Configured Video Device" 
EndSection 

Section "InputDevice" 
	Identifier	"stylus" 
	Driver		"wacom" 
	Option		"Device"	"/dev/input/event6" 
	Option		"Type"		"stylus" 
	Option		"USB"		"on" 
	Option		"Button2"	"3"
EndSection 



Section "ServerLayout" 
	Identifier		"Default Layout" 
	Screen		"Default Screen" 
	InputDevice	"stylus"	"SendCoreEvents" 
EndSection

```

And that's all I needed in my xorg.conf. I restarted X (Ctrl+Alt+Backspace or sudo /etc/init.d/gdm restart) and everything worked.

Notice that instead of the pci path, I just used event6.

I ran wacomcpl to setup buttons, callibration, etc. and followed Favux's instructions for retaining them after a reboot.

I also followed my own instructions to make the front buttons and function keys work. I have yet to mess with rotation. That will be next.

I certainly hope this makes things easier for other Toughbook/Tablet/Wacom users.

My only question is, how can we get all of this info into one place?

---

### Post by Rendrago on 2009-01-25
Well my event number changed twice now. Anyone have any idea what makes these change?

---

### Post by Favux on 2009-01-25
Hi Rendrago,

Outstanding!  Yes.  I gather you want to add the "event 6" information to the tutorial.  Amazingly I ran into a Dell Latitude XT user who was using the full paths for stylus and eraser but "event 3" for touch!  So I was going to check it out.  Now you're confirming it.  It sure would make the xorg.conf cleaner.

In terms of dmesg.  We're grepping the kernel buffer after all.  I have noticed changes, when talking to others.  If they have docks, or usb hubs, or usb devices attached.  But I really haven't been able to get a good handle on it.  Because of my ongoing problem with NM I can only query for a while after boot.  So I do it right after a boot.  Do you think I should add this to the HOW TO, ie only query after fresh boot?  When the event number changes do you loose stylus or whatever?  The latitude user didn't seem to have that problem.

I read your HOW TO quickly, so I may have missed other points you wanted made.  I'll come back and read it more carefully later.

Again great work.

---

### Post by Rendrago on 2009-01-25
> When the event number changes do you loose stylus or whatever?

Yep, change it to the appropriate number and it works again.

---

### Post by Favux on 2009-01-26
Hmmm, then it's not that useful, is it?  I'll try to check it out with the latitude guy.  See if he loses touch intermittently.  Suddenly your wanting to know why the event number changes acquires new urgency.



**Edit re post below:**Please keep us posted!  Oh by the way, is the appropriate number still "event 6"?

---

### Post by Rendrago on 2009-01-26
You are correct. Not very useful at all if it keeps changing, but it seems to stay the same after the initial setup. I'll keep an eye on it.

---

### Post by Favux on 2009-01-27
Hi Rendrago,

I agree with you that simplifying the input path problem would be a good thing.  I've been going at it a different way.  See post #9 at:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

I think it may have some useful information for you.

---

