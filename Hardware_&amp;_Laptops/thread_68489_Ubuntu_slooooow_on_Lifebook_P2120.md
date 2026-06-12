---
title: "Ubuntu slooooow on Lifebook P2120"
date: 2005-09-23
forum: Hardware &amp; Laptops
---

### Post by zhx on 2005-09-23
Hello, I recently switched from Windows 2000 to Ubuntu on my ultraportable Lifebook P2120 and I love the OS itself, but am surprised at how sluggish it performs on my system.

As an ultraportable (and a couple years old), the P2120 doesn't have impressive specs, but Fujitsu claims it was "designed for Windows XP". Well, Windows XP is *bearable* on it, but Windows 2000 runs great. I was hoping to squeeze a little more performance out of it by switching to what I thought would be a more lightweight operating system. Ubuntu runs MUCH slower than XP does on it, and that makes absolutely no sense. Even Firefox seems to render pages slowly, which was never a problem in Firefox under 2K.

Surely, this has to be something that could be ironed out with some tweaking, but I've found very little on the forums about performance adjustments. So I guess my question is: Is there something in software I can do to improve Ubuntu's performance, or is Ubuntu that much more taxing on a system than Windows 2000 (or even XP)? I would find that difficult to believe.

I think Ubuntu is a perfect compliment to my laptop, but it's difficult to commit myself to really digging into the OS's guts when it can take up to 3 seconds for the applications menu to pull down, for example.

Here's my laptop's (relevant) specs:
933mhz Transmeta Crusoe CPU
384mbs RAM
40gb HDD

Thanks.

---

### Post by doog on 2005-09-23
[QUOTE=zhx]
Here's my laptop's (relevant) specs:
933mhz Transmeta Crusoe CPU
384mbs RAM
40gb HDD

Thanks.[/QUOTE]

The graphics chip and possibly the system chipset are going to make a big difference so you'll want to post that info too. Video is a big part of a systems performance and if your IDE hard drive is not using DMA and 32bit access, it'll slow things down too.

---

### Post by zhx on 2005-09-23
Ohhhhh yeah, I completely spaced that. That would make sense, as my laptop is very weak in the graphics department. It's an ATI Radeon Mobility with only 8mbs RAM.

Is there anything I can do to optimize for very little video RAM? Maybe my ATI drivers aren't installed or configured properly? How can I tell what driver my system is using?

Also, the system is based around the ALi M1535 chipset. I know nothing about its capabilities.

---

### Post by nbcthreat on 2005-12-24
Here's the other thing. That transmeta chip is unique. It emulates x86 by recompiling code on the fly. It's interesting. The good news is that it is possible for Linux to take advantage of little hooks that can make it run faster on a transmeta CPU. You'll want to compile a custom kernel that is optimized for the transmeta CPU. That's actually a lot easier than it sounds and you should see a major performance improvement.

[https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28recompile%29%7C%28kernel%29](https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28recompile%29%7C%28kernel%29)

Additionally, you should do a search for "transmeta" on synaptic. You'll find the transmeta longrun control program that will let you tweak the CPU for battery life or performance. Let me know how it turns out. I'm interested in getting one of these.

---

### Post by countryboy on 2006-04-23
[QUOTE=nbcthreat]Here's the other thing. That transmeta chip is unique. It emulates x86 by recompiling code on the fly. It's interesting. The good news is that it is possible for Linux to take advantage of little hooks that can make it run faster on a transmeta CPU. You'll want to compile a custom kernel that is optimized for the transmeta CPU. That's actually a lot easier than it sounds and you should see a major performance improvement.

[https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28recompile%29%7C%28kernel%29](https://wiki.ubuntu.com/KernelCompileHowto?highlight=%28recompile%29%7C%28kernel%29)

Additionally, you should do a search for "transmeta" on synaptic. You'll find the transmeta longrun control program that will let you tweak the CPU for battery life or performance. Let me know how it turns out. I'm interested in getting one of these.[/QUOTE]

I have a P2120 and I also found it to be very very slow. I have installed the longrun utility, but I don't notice any difference in the speed of the unit :(

---

### Post by reh4c on 2006-08-01
Hello.  I successfully enabled DRI on the terribly slow Rage Mobility P/M graphics chip on my Fujitsu LOOX T86A (Japanese model).  I posted a big report/how-to in the Malone bug tracker.  Just do a search for ATI Rage Mobility and DRI.  It may help some.

---

### Post by warp99 on 2008-01-20
I just recently was given a P2120 and after some trial and error I was able to enable DRI and longrun to speed up the performance. Here is exactly what I did:

First I made some BIOS settings changes with regards to the video card:

1) During POST hit F2 then go to Advanced > Video Features
2) Change "Compensation" to "Enabled"
3) Change "Video Speed Mode" to "Performance" unless for want more battery life then leave this setting at "Power Savings"
3) F10 to save then exit

Next we need to enable DRI as that's done by changing the resolution and color depth. Normally xserver obtains the information from the BIOS and sets the resolution to 1280x768 at a color depth of 24. Since the laptop only had 8mb of video ram DRI will not load and an error message in Xorg.0.log shows up stating you need 9000kb of video ram.

First we need to load the correct libraries:
```
 sudo apt-get install libgl1-mesa-dri libgl1-mesa-glx
```

Back up your xorg.conf file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Then edit xorg.conf to change the resolution and color depth:
```
sudo nano /etc/X11/xorg.conf
```

Scroll down to the "Screen" section of your xorg.conf. It should looks something like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M6 LY"
        Monitor         "Laptop Flat Screen"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

Change the settings DefaultDepth to 16 then remove, add, or change the mode "1280x768" to "1250x750" and finally add the line Virtual in the SubSection "Display" area with a maximum desktop settings of 1250 750. When completed your xorg.conf it should look like this:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc Radeon Mobility M6 LY"
        Monitor         "Laptop Flat Screen"
        DefaultDepth    16
        SubSection "Display"
                Modes           "1250x750" "1024x768" "800x600" "640x480"
                Virtual          1250 750
        EndSubSection
EndSection

```

Save the file then restart X and check your Xorg.0.log to confirm DRI is enabled:
```
cat /var/log/Xorg.0.log |grep enabled
```

Your output should look like this:

```
(==) AIGLX enabled
(II) RADEON(0): Color tiling enabled by default
(II) RADEON(0): Direct rendering enabled
(II) RADEON(0): Render acceleration enabled
(II) RADEON(0): Acceleration enabled
(**) RADEON(0): DPMS enabled
(==) RADEON(0): Silken mouse enabled
(II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.

```

If you like you can also change the resolution in usplash.conf to make the terminal resolution consistent with your desktop:

```
sudo nano /etc/usplash.conf
```

and change the resolution to the following:
```
# Usplash configuration file
xres=1250
yres=750

```

then reconfigure usplash which will run update-initramfs and set the correct resolution on reboot:
```
sudo dpkg-reconfigure usplash
```

I also enabled the longrun utility using this ubuntu help guide:

[https://help.ubuntu.com/community/LongRunHowTo](https://help.ubuntu.com/community/LongRunHowTo)

You can make a boot script to load the utility at startup up if your like. There are various guides on the forums to show you how.  :)

---

### Post by ilovebsod on 2008-01-24
hi Warp99,

what repositories are you getting those libraries from?

with just the default repositories I get that the package can't be found for both libgll-mesa-dri and libgll-mesa-glx

Thanks!

---

### Post by warp99 on 2008-01-24
They should be in the default repositories. They are listed at packages.ubuntu.com in the main section here:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgl1-mesa-dri&searchon=names&subword=1&version=all&release=main](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgl1-mesa-dri&searchon=names&subword=1&version=all&release=main)

and here:

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgl1-mesa-glx&searchon=names&subword=1&version=all&release=main](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=libgl1-mesa-glx&searchon=names&subword=1&version=all&release=main)

I would check to see that you have a main section listed in your sources file. Just run the following command:

```
cat /etc/apt/sources.list |grep main
```

You should have an output something like this:

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

You should have a main section, otherwise you wouldn't get any updates. ;)

---

### Post by JarrettV on 2008-01-28
> **warp99 said:**
> I just recently was given a P2120 and after some trial and error I was able to enable DRI and longrun to speed up the performance

First a note on the packages: that is a "one" rather than a double L

ibgl**1**


I have some questions:

Can you post your entire xorg.conf file?

Did you choose 1250x750 rather than 1280x768 to save some video memory?

Are you using the built in video drivers?

Is there a performance test we can run to compare speed?

Thanks,

---

### Post by warp99 on 2008-01-28
> First a note on the packages: that is a "one" rather than a double L

I assume that was directed towards ilovebsd and not me.

>  Can you post your entire xorg.conf file?

Not a problem, here you go:

```
# xorg.conf (xorg X Window System server configuration file)
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

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"altwin:super_win"
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

Section "Device"
	Identifier	"ATI Technologies Inc Radeon Mobility M6 LY"
	Driver		"ati"
	BusID		"PCI:0:20:0"
EndSection

Section "Monitor"
	Identifier	"Laptop Flat Screen"
	Option		"DPMS"
	HorizSync	28-33
	VertRefresh	43-72
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M6 LY"
	Monitor		"Laptop Flat Screen"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1250x750"
		Virtual		1250 750
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

```

> Did you choose 1250x750 rather than 1280x768 to save some video memory?

If you want hardware acceleration enabled you have to lower the screen resolution and the color depth otherwise you'll get an error in Xorg.0.log stating you need 9000kb of video memory to load the DRI module. With the DRI module loaded your system is now using video hardware acceleration instead of software emulation so you're not really savings any video memory, just getting the hardware acceleration to work. This of course shifts resources away from the processor and system ram.

> Are you using the built in video drivers?

Using the open ATI drivers straight from the repositories:

xserver-xorg-video-ati

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=+xserver-xorg-video-ati&searchon=names&subword=1&version=all&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=+xserver-xorg-video-ati&searchon=names&subword=1&version=all&release=all) 

> Is there a performance test we can run to compare speed?

I haven't come across a test for the transmeta chip you can run, but you can check the video performance using glxgears. 

The only problem that I have incurred is that by running in 16-bit color depth Totem and Mplayer would only show a blue screen until I changed the video driver from xv to x11. Also video that runs at a depth of 24 doesn't seem to work properly with Totem and Mplayer since both seem to have a problem with color reduction. To solve this I just installed VLC, set the driver to x11, and allowed for frame dropping. Now I can view almost any video and even watch fullscreen DVDs without too many frame dropouts. :)

---

### Post by kcnnc on 2008-06-30
I was trying to get Ubuntu Desktop 8.04 to install on the P2120 and it was really slow. It keeps reading the disk and took a long time between each step. Finally in step 7 it just stops at 15% (scanning disk).

How did you guys get Ubuntu to install in the first place?

---

### Post by kcnnc on 2008-07-04
Got it installed using the alternate desktop CD.

It seems like on 8.04 there is no error message in Xorg.0.log about needing 9000kb of video ram.

---

