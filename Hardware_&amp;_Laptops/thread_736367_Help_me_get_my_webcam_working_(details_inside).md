---
title: "Help me get my webcam working? (details inside)"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by Redrazor39 on 2008-03-26
Hi, I have a Sony VAIO VGN-SZ430N model with a webcam and I need help because I am running Ubuntu 7.10. I also plan to upgrade to Ubuntu 8.04 soon after it comes out so I may need help with that (if it doesn't already work).

This is the output for lspci:
```

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G72M [GeForce Go 7400] (rev a1)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
07:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 16)
09:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
09:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
09:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```

and this is the output for lsusb, but my webcam is built in (or does that even matter?):
```
Bus 002 Device 001: ID 0000:0000
Bus 003 Device 002: ID 046d:c521 Logitech, Inc.
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 004 Device 001: ID 0000:0000
Bus 005 Device 002: ID 044e:300d Alps Electric Co., Ltd
Bus 005 Device 001: ID 0000:0000
Bus 001 Device 003: ID 054c:0281 Sony Corp.
**Bus 001 Device 005: ID 05ca:1835 Ricoh Co., Ltd**
Bus 001 Device 001: ID 0000:0000
```
*I'm fairly sure the one in bold is my webcam.*
One of those is my mouse (right now I have a logitech USB wireless mouse plugged in)

Please post any solution for Ubuntu 7.10, and, if necessary and possible, one for Ubuntu 8.04.

---

### Post by linuxwizard on 2008-03-26
Have you just tried using your webcam with any apps. to see if it would work ? Try using Ekiga see if the cam works/detected. You may have to work with the settings > Open Ekiga > Edit > Preferences > Video > Video Devices > try changing some of the settings. 
To test your webcam you can do this:
There are 6 icons on the left side of the main Ekiga window. Push the 4th button from the top (a grey round webcam). If eveything is ok, you'll see the output of the webcam. If not, you'll see the Ekiga logo bouncing.

---

### Post by Redrazor39 on 2008-03-26
I've tried it with Cheese, Camorama, and what you said. They all failed.

/dev/video0 or something is not detected in some

---

### Post by linuxwizard on 2008-03-26
Cheese & Camorama that does not surprise me. Did you try Ekiga ? That is the best way to see if your cam is going to work more settings to work with and adjust. Alot of cams will just work others you will need to install drivers. Lets see if cam works first.

---

### Post by Redrazor39 on 2008-03-26
yea, it only showed the ekiga logo floating up and down :(

---

### Post by linuxwizard on 2008-03-26
This is the driver you need. It shows your cam listed in the supported devices. > [http://wiki.mediati.org/R5u870](http://wiki.mediati.org/R5u870)

---

### Post by Redrazor39 on 2008-03-26
Wow! Thanks! but I don't really understand the installation instructions. Are those the full commands or do I need to fill in filenames somewhere?

Here:

**Installation**

This section describes the steps required to install the driver from source, so you can get up and running with your favorite webcam-utilising applications!
[edit] Packages

If you're looking on installation instructions from packages, please see r5u870/Packages.
[edit] Prerequisites

You will need:

    * Either kernel headers, or complete kernel source for your target kernel. Your kernel must be version 2.6.17 or newer.
    * Tools to compile the driver - normally in the build-essentials package or similar. This includes gcc, make, autotools, etc.
    * A webcam supported by the driver (see above).
    * A brain. 

[edit] Compiling

Change the current working directory into the directory in which you have placed the module sources, and execute:

$ make

You can pass KDIR=<path> to specify a specific kernel location, as such:

$ make KDIR=/usr/linux-2.6.23-rc1/

[edit] Installing

To install the driver onto the system, simply run:

# make install

If you ran make with a different kernel path, you should specify it on the command line when installing, too.

Installed modules will be automatically probed for supported devices by the udev coldplug component at boot, and the driver should be automatically loaded on subsequent reboots.

If this is not the case, just add the modulename into a file inside of /etc/modules.d, to load the device on boot.
[edit] Loading the driver

If you installed the driver, you can just run:

modprobe r5u870

If you wish to load the driver without installing it, you must load the prerequisite modules:

modprobe usbcam
modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32		(on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:

insmod r5u870.ko

---

### Post by Redrazor39 on 2008-03-29
hello? can't anyone translate please?

---

### Post by ringhio06azzurro on 2008-03-30
I have the same problem, I'm using a Sony Vaio vgn-cr123e and that's the driver I want. No idea how to install it. Any help would be greatly appreciated!

---

### Post by Redrazor39 on 2008-03-30
If only someone could see this and understand it and just type out the exact commands for the 1835 version because I don't know what most of this stuff means.

---

### Post by ringhio06azzurro on 2008-03-30
Can we post this question to an administrator somehow? Direct someone's attention to this thread?

---

### Post by Redrazor39 on 2008-03-31
I don't know, but you may be able to contact an admin via PM and link them to this thread.

---

### Post by InfernalNeutrino on 2008-04-14
Hi!

So I'm a fellow neophyte Ubuntu user who is also trying to get his webcam running - and I think I have succeeded with the instructions this thread has been trying to decypher! So, I'm going to show my interpretation of the instructions in hopes that it helps another ubuntu newbie out there :). While reading, please keep in mind that I'm very new to the wonders of non-windows/mac operating systems, and so my knowledge base is completely limited to "well, this seemed to work...."

Ok, here we go. I'm just going to comment on each step of the instructions under discussion:

[edit]  Download

If you build from source, you you'd like the latest version of the driver, you'll need to check the driver out of Subversion:

svn co [http://svn.mediati.org/svn/r5u870/trunk](http://svn.mediati.org/svn/r5u870/trunk) r5u870

Stable releases can be checked out of SVN using the STABLE_CURRENT tag instead of trunk.

A tarball of the latest stable version is also available here (version 0.11.0).

Instructions for packages are mentioned below. 

[I][COLOR="Red"]you need to have svn installed for this to work. You can get it by typing this in a terminal:
$ sudo apt-get install subversion[/COLOR]
[/I]


[edit]  Installation

This section describes the steps required to install the driver from source, so you can get up and running with your favorite webcam-utilising applications!

*[COLOR="Red"]nothing interesting here...[/COLOR]*

[edit] Packages

If you're looking on installation instructions from packages, please see r5u870/Packages.

*[COLOR="Red"]I looked at those, but just got confused so I stuck with installing from source...[/COLOR]*

[edit] Prerequisites

You will need:

    * Either kernel headers, or complete kernel source for your target kernel. Your kernel must be version 2.6.17 or newer.
    * Tools to compile the driver - normally in the build-essentials package or similar. This includes gcc, make, autotools, etc.
    * A webcam supported by the driver (see above).
    * A brain. 

[I][COLOR="Red"]This was initially confusing, but it seems that what he really is saying is that you need a functioning operating system and a supported webcam. The one important thing is that your kernel must be 2.6.17 or newer, so just check by typing the following in a terminal:

$ uname -r

When I do that, I get the following output:
2.6.22-14-generic

So it seems that my kernel is newer and therefore usable. Yay![/COLOR]
[/I]

[edit] Compiling

Change the current working directory into the directory in which you have placed the module sources, and execute:

$ make

You can pass KDIR=<path> to specify a specific kernel location, as such:

$ make KDIR=/usr/linux-2.6.23-rc1/

[I][COLOR="Red"]Scary! So, all he really seems to mean is that we want to compile. If you are like me and really don't know about the subtleties of kernels and such, the default "make" command should be fine. Long story short: all he really wants you to do is move to the directory that you downloaded the driver to and type "make." Since I move the driver download to ~/Desktop/Random/software/r5u870 it looked like this for me:

$ cd ~/Desktop/Random/software/r5u870
$ make[/COLOR]
[/I]

[edit] Installing

To install the driver onto the system, simply run:

# make install

If you ran make with a different kernel path, you should specify it on the command line when installing, too.

Installed modules will be automatically probed for supported devices by the udev coldplug component at boot, and the driver should be automatically loaded on subsequent reboots.

If this is not the case, just add the modulename into a file inside of /etc/modules.d, to load the device on boot.

[edit] Loading the driver

If you installed the driver, you can just run:

modprobe r5u870

If you wish to load the driver without installing it, you must load the prerequisite modules:

modprobe usbcam
modprobe videodev
modprobe video-buf
modprobe v4l1-compat
modprobe v4l2-common
modprobe compat_ioctl32		(on 64-bit platforms)

You must also copy the microcode files (r5u870_*.fw) to /lib/firmware.

Then you may load the module manually:

insmod r5u870.ko

[I][COLOR="Red"]That was also scary. The basic idea is that we want to install this thing so it'll work! For me, that looked like this:

$ sudo make install
$ sudo modprobe r5u870

Note that I had to use sudo! It didn't let me install until I did that. Otherwise file permissions get all mad at you. All the rest of the stuff the instructions say is irrelevant for just installing and using the driver the way a simpleton like me wants to (or so it seems). After doing all this, my webcam was recognized by skype and gave me a nice preview, so I think it's working properly. Good luck![/COLOR]
[/I]

---

### Post by charlemagne86 on 2008-05-23
HEY EVERYONE

for all those people who have got their webcams working on ekiga but after a sec or so they begin showing distortions with funny black/red/pink/green colors.....i found a sollution:

when you start ekiga webcam, when this distortion happens....just clik on the brightness slider in the video tab (even the minutest adjustment will do) and the distortions are all gone...even after you restart ekiga again....However you have to do this after each reboot.

---

