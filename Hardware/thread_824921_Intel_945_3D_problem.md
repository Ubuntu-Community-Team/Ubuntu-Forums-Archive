---
title: "Intel 945 3D problem"
date: 2008-06-10
forum: Hardware
---

### Post by tekwerx on 2008-06-10
Hi all.  I have bought a new laptop - an Everex SA2053T.  I knew I couldnt put Linux on it until a few bugs got worked out with the kernel, because of the built-in SD card reader.  No big deal.  I waited, and those problems are now solved, as with 8.04 I can now install.  My problem now is, I cannot get any 3D accel.  I did some searching, and found [http://ubuntuforums.org/showthread.php?t=735539](http://ubuntuforums.org/showthread.php?t=735539).  Ok, well, this lets me know there is a problem, but its not for my specific hardware I guess.  Instead of having "8086:27ae", I have "8086:27a2".  Does anyone know how to fix this?  It would be greatly appreciated, as this is the only thing keeping me from finally getting rid of the other crappy OS on this machine.  In the .conf, all it shows is "Configured Video Device".  Thanks all in advance for the help.

---

### Post by stchman on 2008-06-10
> **tekwerx said:**
> Hi all.  I have bought a new laptop - an Everex SA2053T.  I knew I couldnt put Linux on it until a few bugs got worked out with the kernel, because of the built-in SD card reader.  No big deal.  I waited, and those problems are now solved, as with 8.04 I can now install.  My problem now is, I cannot get any 3D accel.  I did some searching, and found [http://ubuntuforums.org/showthread.php?t=735539](http://ubuntuforums.org/showthread.php?t=735539).  Ok, well, this lets me know there is a problem, but its not for my specific hardware I guess.  Instead of having "8086:27ae", I have "8086:27a2".  Does anyone know how to fix this?  It would be greatly appreciated, as this is the only thing keeping me from finally getting rid of the other crappy OS on this machine.  In the .conf, all it shows is "Configured Video Device".  Thanks all in advance for the help.

Give us an lspci output.  The Intel GMA video cards should work OOB with Hardy.  I have an X3100 and it works very well.

---

### Post by tekwerx on 2008-06-10
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

---

### Post by stchman on 2008-06-10
> **tekwerx said:**
> 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
03:04.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
03:06.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
03:06.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
03:06.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)

That controller should work just fine with Compiz.  Ubuntu Hardy uses mesa which in an open source version of openGL.

---

### Post by tekwerx on 2008-06-10
Section "Device"
	Identifier	"Configured Video Device"
EndSection


Thats it for the video.  No Intel, no nothing.  When I try to bring up anything 3D accellerated, even something like a screensaver, the whole machine basically freezes up.  I can move the mouse a couple of inches every few seconds to close the box, then things go back to smooothly working normal.  Judging from this, I have no drivers installed, even though I should.  As with the other post I linked to above, they had the same problem, but with slightly different hardware.

---

### Post by stchman on 2008-06-10
> **tekwerx said:**
> Section "Device"
	Identifier	"Configured Video Device"
EndSection


Thats it for the video.  No Intel, no nothing.  When I try to bring up anything 3D accellerated, even something like a screensaver, the whole machine basically freezes up.  I can move the mouse a couple of inches every few seconds to close the box, then things go back to smooothly working normal.  Judging from this, I have no drivers installed, even though I should.  As with the other post I linked to above, they had the same problem, but with slightly different hardware.

Try installing this package.

```
sudo apt-get install xserver-xorg-video-intel
```

It is the display driver for Intel i8xx and i9xx cards.  I remember I had to install that package when I was messing around with a GMA950 card in a laptop.

[http://packages.ubuntu.com/hardy/xserver-xorg-video-intel](http://packages.ubuntu.com/hardy/xserver-xorg-video-intel)

---

### Post by tekwerx on 2008-06-10
Installed.  Do I need to do the dpkg-reconfigure now to get it to start using it?  I rebooted but I still have the "no proprietary drivers in use" message.

---

### Post by stchman on 2008-06-10
> **tekwerx said:**
> Installed.  Do I need to do the dpkg-reconfigure now to get it to start using it?  I rebooted but I still have the "no proprietary drivers in use" message.

It should just work.  That package is not proprietary it is open source.

---

### Post by tekwerx on 2008-06-10
Ah, ok.  Didnt not know that.  Still having the same problems though.  As long as I dont have any 3D accel, everything is smooth.  The moment I try anything 3D, the screen decides it likes 1 FPS.

---

### Post by tekwerx on 2008-06-10
*bump*  Anyone?

---

### Post by tekwerx on 2008-06-10
...alright.  Thank you for your help.  Its been very appreciated.  Blessings to you all.

---

### Post by SaintStewart on 2008-06-10
*bump*

---

### Post by SaintStewart on 2008-06-11
*bumpetty bump*

---

### Post by SaintStewart on 2008-06-11
*sigh* Yet another bump.

---

### Post by BandD on 2008-06-12
Can you post the output of:

```
grep Driver /var/log/Xorg.0.log
```

This will tell you what driver xorg is using.  Things have changed a bit with xorg configuration in Hardy.  I still don't really understand it all, but basically the xorg.conf file is left very basic and xorg basically autodetects everything.  So I want to be sure that xorg is selecting the right driver.  And that code will tell us what driver it is using.

---

### Post by tekwerx on 2008-06-12
X.Org Video Driver: 2.0
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org Video Driver
	ABI class: X.Org Video Driver, version 2.0
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
	Module class: X.Org XInput Driver
(II) intel: Driver for Intel Integrated Graphics Chipsets: i810,
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
	ABI class: X.Org Video Driver, version 2.0
(II) EXA(0): Driver registered support for the following operations:

---

### Post by tekwerx on 2008-06-12
*bump*

---

### Post by imon9 on 2008-06-12
i got mine solve...here is a fiw tips, if u follow them, u should be able to run compiz:
(1) uninstall xserver-xgl (if u have any)
(2) use this version of compiz-check to check ur system [http://forlong.blogage.de/article/pages/Compiz-Check](http://forlong.blogage.de/article/pages/Compiz-Check)
(3) install libgl1-mesa-dri (according to the bugzilla, hardy now depends on this to make compiz works)

REBOOT! see if compiz works

IF it doesnt, u may have to tweak ur /etc/X11/xorg.conf

i will attach mine for ur reference (note, this in not a full entry, i only provided the relevant sections.

```

Section "Device"
	Identifier	"Intel i810"
	Driver		"intel"
	BusID 		"PCI:0:2:0"
 	Option 		"XAANoOffscreenPixmaps"	"true"
 	Option 		"AllowGLXWithComposite"	"true"
	Option 		"AddARGBGLXVisuals" 	"true"
 	Option 		"DisableGLXRootClipping"	"true"
	Option		"AIGLX"			"On"
	Option          "DRI"     		"true"
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
	Option		"AIGLX"	"On"
EndSection

Section "Extensions"
   	Option   	"Composite"	"Enable"
EndSection

Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"dri"
	Load		"v4l"
EndSection

```

make a comparison and add whatever you doesnt have.

---

### Post by shusai on 2008-06-12
Thanks a lot, imon9!:)

After upgrading Ubuntu on my Panasonic Let's Note Light Y5 to 8.04 all my videos played slowly like a "slide-show", mplayer told me "Your system is too SLOW to play this!" and glxgears showed about 20 FPS.

The last 2 weeks I tried to find a solution, played with different drivers, settings, installed Ubuntu about 10 times but nothing helped.](*,)

I already wanted to throw my notebook out of the window, but thanks to your /etc/X11/xorg.conf tweak finally everything works!

xserver-xgl was not installed on my system, libgl1-mesa-dri already was, so I just made the changes to /etc/X11/xorg.conf.

Now videos run like a charm and glxgears shows almost 400 FPS.

Thank you!!
=D>=D>=D>=D>=D>=D>

---

### Post by tekwerx on 2008-06-12
Bah.  Still not working for me.  After taking a couple of days and really searching around, I beleive that my revision of the video isn't supported yet, although I beleive it will be next month with "SP1" that comes out about the 10th.  Ah well.  Till then, Im stuck with no 3D.  I'll just have to keep dual booting till then.  Thank you all for helping and trying.  Its extremely appreciated.

---

### Post by imon9 on 2008-06-13
tekwerx,

first, make sure your installation is up-to-date!
meaning, under synaptics > pakages > software-sources > updates >
checkall type of "ubuntu updates"
> important security updates
> recommended updates
> pre-release updates
> unsupported updates
(WARNING!!! since this include pre-release & unsupported updates, it includes the latest bug fix, but it might also include the latest bug.... so u have to think about the stability of your computer IF u use the computer for important work. Else, go ahead... mostly it is stable) 

secondly, did u did the compiz-check (downloaded fromt the link above?). does it return all ok?
your compiz might not work becoz u have activated some other window manager to replace compiz before this. if that is so, compiz-check can help u correct that..

thirdly, u can try copy-paste those sections of my xorg.conf (see above) to replace yours.
seriously, your graphic card support compiz.

also, please check the command ```
$ glxinfo | grep direct
``` 
and paste it here... supposingly, it return direct rendering = yes (if your xorg.cof is configured correctly)

if there is any error. please post here again. if u still want to try

---

### Post by tekwerx on 2008-06-13
> **imon9 said:**
> tekwerx,

first, make sure your installation is up-to-date!
meaning, under synaptics > pakages > software-sources > updates >
checkall type of "ubuntu updates"
> important security updates
> recommended updates
> pre-release updates
> unsupported updates
(WARNING!!! since this include pre-release & unsupported updates, it includes the latest bug fix, but it might also include the latest bug.... so u have to think about the stability of your computer IF u use the computer for important work. Else, go ahead... mostly it is stable) 

secondly, did u did the compiz-check (downloaded fromt the link above?). does it return all ok?
your compiz might not work becoz u have activated some other window manager to replace compiz before this. if that is so, compiz-check can help u correct that..

thirdly, u can try copy-paste those sections of my xorg.conf (see above) to replace yours.
seriously, your graphic card support compiz.

also, please check the command ```
$ glxinfo | grep direct
``` 
and paste it here... supposingly, it return direct rendering = yes (if your xorg.cof is configured correctly)

if there is any error. please post here again. if u still want to try



Yep.  Im all up to date.  Fresh install.  I *do* have direct rendering = yes.  I tried to use your .conf, but when I rebooted, it gave me the card could not be configured dialog that had me choose a new card, because X could not be started.  So I reverted the .conf, and I could at least see again.  Seriously, from what Ive read, its just a line or two of code that needs to be added in somewhere because I have a newer revision of the 945GM.  I just will wait it out till July 10th (I think it was?) when they do the .1 service pack or whatever its called for Ubuntu.  If someone can fix it before then, great.  If not, no big deal.  Thanks.  :)

---

### Post by SaintStewart on 2008-07-11
Time to resurrect this thread.  Ive got the same problems, with the same machine - an SA2053T.  As per the instructions in [http://ubuntuforums.org/showthread.php?t=735539](http://ubuntuforums.org/showthread.php?t=735539) and [https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver), I have tried since this thread started to get my video working correctly.  Epic fail.  No 3D anything.  The moment I try to do anything 3D (Compiz, Screensavers, anything), the screen slows down to where I can't do anything and the mouse moves once every few seconds. I know theres something wrong with the video driver, but I cant force it to work.  I do lspci -vn | grep VGA | awk '{ print $3 }' and get the output of 8086:27a2, as per teflon227 (post #26) in the first link.  Like him, no matter what I do, it will not allow me to choose any video drivers to actually get any 3D accelleration.  The Xorg.conf file just says 

Section "Device"
	Identifier	"Configured Video Device"
EndSection.

I go to Applications > Other > Screens and Graphics and try to assign the driver to i810, but once chosen, the box will remain blank, and when I choose test just to see if it will do anything, it of course says test failed.  

Im pulling my hair out, as I *know* that this video will work fine, as with plain Debian and Kubuntu, both of them will assign the correct driver and it will work perfectly. Yes, I can hear you now - "just use one of those then".  I want to use Ubuntu.  I like the community, and the OS - the two reasons I want to use it.  So please, help me figure this out.  Thanks in advance, sorry for being so long winded and if theres anything I need to clarify....please let me know.  I'll post it here.

---

### Post by SaintStewart on 2008-07-11
*bump*

---

### Post by SaintStewart on 2008-07-12
Ok, well, I can see that I was mistaken about the community.  I'll be going back to Windows. Take care, and good luck with the open source thing.

---

