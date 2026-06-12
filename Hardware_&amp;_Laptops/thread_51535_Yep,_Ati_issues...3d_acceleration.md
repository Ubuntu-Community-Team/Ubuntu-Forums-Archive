---
title: "Yep, Ati issues...3d acceleration"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by Atomic on 2005-07-24
Hi,

i correctly installed the latest ati drivers for xorg, got the kernel headers installed and everything, but 3d acceleration won't work properly -or at all.
My Kernel-Version:
2.6.10-5-386 
I did the fglrxconfig stuff several times.
I am running Ubuntu 5.04 on an amd athlon 2500+, Radeon 9500, Asrock k7v88.
this is the error-code in my xorg.0.log:


(II) fglrx(0): Kernel Module Version Information:
(II) fglrx(0):     Name: fglrx
(II) fglrx(0):     Version: 8.8.25
(II) fglrx(0):     Date: Jan 14 2005
(II) fglrx(0):     Desc: ATI FireGL DRM kernel module
(WW) fglrx(0): Kernel Module version does *not* match driver.
(EE) fglrx(0): incompatible kernel module detected - HW accelerated OpenGL will not work
(II) fglrx(0): [drm] removed 1 reserved context for kernel
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0xe0c6e000 at 0xb7db0000
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *
(II) fglrx(0): FBADPhys: 0xc0000000 FBMappedSize: 0x08000000
(II) fglrx(0): FBMM initialized for area (0,0)-(1280,8191)
(II) fglrx(0): FBMM auto alloc for area (0,0)-(1280,1024) (front color buffer - assumption)
(==) fglrx(0): Backing store disabled
(==) fglrx(0): Silken mouse enabled

any suggestions?

Thanks in advance,

Martin

---

### Post by tbasten on 2005-07-24
exacly the same as me. I got a thread already start. Help seems hard to get :(. Stupid ATI. Nvidia was so much easier to install

---

### Post by Atomic on 2005-07-24
[QUOTE=tbasten]exacly the same as me. I got a thread already start. Help seems hard to get :(. Stupid ATI. Nvidia was so much easier to install[/QUOTE]


ATI on Ubuntu sucks. I could throw up all over my keyboard - it took me 2 days to get more than 60Hz refresh...
And all this trial&error stuff! All that i want is working 3d - or i'll switch to XP again, i swear! :-)

---

### Post by tbasten on 2005-07-24
LOL, i installed Windows last night on another hdd just so i could play wow because people on IRC didnt want to help me. The Wiki's are usless, i tryed compiling a new kernel. eerors there, tryed about 10 other things and still no hardware rendering ](*,)

---

### Post by Zeroedout on 2005-07-24
[QUOTE=tbasten]LOL, i installed Windows last night on another hdd just so i could play wow because people on IRC didnt want to help me. The Wiki's are usless, i tryed compiling a new kernel. eerors there, tryed about 10 other things and still no hardware rendering ](*,)[/QUOTE]

outta sheer curiousity, did you guys, all of you, try moving the compiled module to the right location? First thing i did was uninstall the old fglrx, then download all the stuff that i needed to compile the new one. Once you use ati's installer to 'install' the module, it places it in a location where ubuntu dosn't use for drivers. You have to move it to the right location. Search the forums for posts by me, and you'll see one that will tell you exactly where (and how) to move the .ko file. 

I can't speak for others, but personally, when some asshole just threatens to move to windows, i really don't feel like talking to them. What OS you use is your choice. If you don't have the patience to set up something that you want working, then move to something else that will allow you do what you need.  I personally game quite a bit, and the ATI drivers will not give you as good a performance as you will get on windows with them, and i am yet to find a way to overclock the card, but i find that a shitload better than virus scans, disk defragment etc..... Threatening to install windows won't grab someones attention (not in a positive light anyway), it just makes you look like an ass, in my opinion anyway.

---

### Post by evilghost on 2005-07-24
Zeroedout, I could live without the profanity, and I think you failed to see the emoticon by the statement about switching to XP.

I was running a 9800 PRO until I switched over to a 6600GT -> 6800GT.  To avoid UT2004 gitters/slowness be sure to get the newest ATI drivers from their site.  Here's a snippet of my Xorg.conf when I was running the newest ATI drivers:


I wish I had better notes on what I did to get them working, but basically:
1) Remove all apt/deb packages for fglrx, or any ATI drivers you installed using apt.
2) Get the kernel-headers and build-essentials stuff.
3) killall gdm, or, boot into single-user mode.
4) sh ATI*.run to run the package, you should be able to build it pretty easily.  I did not have to move the module around like others did.
5) Modify the xorg.conf, here are the valuable snippets from mine:

```

Section "Module"
        Load    "bitmap"
        Load    "dbe"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "record"
        Load    "type1"
        Load    "vbe"
EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon 9800 Pro (R350 NH)"
        #Driver         "ati"
        Driver          "fglrx"
        BusID           "PCI:1:0:0"
        Option          "NoDCC"
        Option          "VideoOverlay"  "on"
        Option          "OpenGLOverlay" "off"
        Option          "UseInternalAGPGART" "no"
        VideoRam        131072
EndSection

```

---

### Post by evilghost on 2005-07-24
Also, remember you can use "gtf" to figure out the "Modeline" value you can use under "Monitor" in the xorg.conf.

Example, my monitor I have configured to run at 1280x1024 @ 100Hz, so here is the modeline I use:

```

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       31-100
        VertRefresh     55-100
        # 1280x1204 @ 100.00 Hz (GTF) hsync: 127.50 kHz; pclk: 226.44 MHz
        Modeline "1280x1204_100.00"  226.44  1280 1384 1528 1776  1204 1205 1208 1275  -HSync +Vsync
EndSection

```

I used the following command to generate the modeline:
```

luser@400sc:/etc/X11$ gtf

usage: gtf x y refresh [-v|--verbose] [-f|--fbmode] [-x|--xorgmode]

            x : the desired horizontal resolution (required)
            y : the desired vertical resolution (required)
      refresh : the desired refresh rate (required)
 -v|--verbose : enable verbose printouts (traces each step of the computation)
  -f|--fbmode : output an fbset(8)-style mode description
 -x|--xorgmode : output an Xorg-style mode description (this is the default
                if no mode description is requested)

luser@400sc:/etc/X11$ gtf 1280 1024 100

  # 1280x1024 @ 100.00 Hz (GTF) hsync: 108.50 kHz; pclk: 190.96 MHz
  Modeline "1280x1024_100.00"  190.96  1280 1376 1520 1760  1024 1025 1028 1085  -HSync +Vsync

```

This should resolve the 60Hz issue.  I was unable to get the Gnome display settings to see anything past 85Hz.

---

### Post by mjkelly on 2005-07-24
Before you do anything at all that evilghost is saying do this
Im gonna cross post this from the other thread im helping whats his name with


Ive tried everything there is to try about this. From these forums to the wiki ubuntu site to IRC even to a couple good debian forums, and noone could help me. I have a Radeon 9250 tho and i talked someone through installed fglrx for a radeon 9800 with these directions:

[https://wiki.ubuntu.com/BinaryDrive...C%28bina](https://wiki.ubuntu.com/BinaryDrive...C%28bina) ry%29

Before you use that guide I would do a couple of things first.

1. Make sure the kernel is the 686 brand. In a console type uname -r Your looking for this 2.6.10-5-686 If it looks like that with the 686 and you already upgraded it to 686 then forget part 1
If it has a 386 at the end, open synaptic and search for linux-image and install the package that looks like this linux-image-2.6.10-5-686
Then install linux-headers-2.6.10-5-686 and linux-restricted-modules-2.6.10-5-686
Restart the computer and load the new kernel. Grub will automatically select it as default.

2. Uninstall the previous fglrx
A simple uninstall of the fglrx driver you have previously installed wont work. Check in /usr/share/fglrx for an uninstall script. I dont know the exact name of it bc i gave up on trying to have it installed. Run the script with "sudo sh fglrx.uninstall.sh" If you cant find the script search the system using "Place > Search for files" and search for fglrx and it should turn up there then go into a console and run that script. It works well. If you cant find that cuz it doesnt existon ur system, search on synaptic for fglrx and uninstall anything thats installed, then do a manual search on the system for fglrx and remove those files as well. If you try to force-overwrite as someone suggested, it doesnt really seem to work. You end up with one type of fglrx here and one type here and it everything gets confusing. Its better to start from scratch in this instance then overwriting from my experience.

3. Then follow this guide here [https://wiki.ubuntu.com/BinaryDrive...C%28bina](https://wiki.ubuntu.com/BinaryDrive...C%28bina) ry%29
Ive seen that guide work but i cant speak for all the other ones. Remember to restart after certain commands like it says to before running the next one.

BTW mine does the exact same thing with the black screen. If you try to play a song before starting the X server, the song even freezes when the server hangs. Someone pointed out to me in one of the Debian chatrooms that this indicated a really hard hang on the system.

On my system, even after the fglrx drivers are installed properly and the kernel accepts them in the kern.log, they still cause it to hang. Ive actually pinpointed it down to a problem caused by DRM and DRI, but thats as far as i tried then gave up after about a week. Lemme know how it goes.

---

### Post by tbasten on 2005-07-24
Thanks for your help. I am at work at the moment so when i get home i will try that out. Yeah my kernel version is 2.6.10-5-386 so i try installing the 686 kernel.

Cheers

---

### Post by sirtoast on 2005-07-26
I'm on an AMD Sempron, should I be still be using 686, or K7?

---

### Post by tbasten on 2005-07-29
yes

---

