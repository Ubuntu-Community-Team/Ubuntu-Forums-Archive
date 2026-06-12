---
title: "Can't get xorg to 1680x1050 resolution on Dell E207WFP with i810 (845G)"
date: 2006-12-27
forum: Hardware &amp; Laptops
---

### Post by bps7j on 2006-12-27
I can't get xorg to give me native widescreen 1680x1050 resolution on this monitor.  Either it thinks it can't do that resolution and falls back to 1280x1024, or it tries a 1680x1050 resolution and the monitor itself refuses to display it.

Hardware details:

```
baron@kansascity:~$ lspci | grep -i graphics
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
```

I started with the usual dpgk-reconfigure and selected some higher resolutions, including 1680x1050.  It displayed 1280x1024@75, and the log file said this:

```
(II) LoadModule: "i810"
(II) Loading /usr/lib/xorg/modules/drivers/i810_drv.so
(II) Module i810: vendor="X.Org Foundation"
   compiled for 7.1.1, module version = 1.6.5
   Module class: X.Org Video Driver
   ABI class: X.Org Video Driver, version 1.0

... snip ...

(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
   i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
   915GM, 945G, 945GM, 965G, 965G, 965Q, 946GZ
(II) Primary Device is: PCI 00:02:0
(--) Chipset 845G found

... snip ...

(II) I810(0): Supported VESA Video Modes:
(II) I810(0): 720x400@70Hz
(II) I810(0): 640x480@60Hz
(II) I810(0): 640x480@75Hz
(II) I810(0): 800x600@60Hz
(II) I810(0): 800x600@75Hz
(II) I810(0): 1024x768@60Hz
(II) I810(0): 1024x768@75Hz
(II) I810(0): 1280x1024@75Hz
(II) I810(0): Manufacturer's mask: 0
(II) I810(0): Supported Future Video Modes:
(II) I810(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
(II) I810(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
(II) I810(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  430 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0

... snip ...

*(WW) (1600x1200,DELL E207WFP) mode clock 162MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,DELL E207WFP) mode clock 175.5MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,DELL E207WFP) mode clock 189MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,DELL E207WFP) mode clock 202.5MHz exceeds DDC maximum 150MHz
(WW) (1600x1200,DELL E207WFP) mode clock 229.5MHz exceeds DDC maximum 150MHz
Mode: 5a (1600x1200)
   ModeAttributes: 0x9b
   WinAAttributes: 0x7
   WinBAttributes: 0x0
   WinGranularity: 64
   WinSize: 64
   WinASegment: 0xa000
   WinBSegment: 0x0
   WinFuncPtr: 0xc0005d0f
   BytesPerScanline: 6400
   XResolution: 1600
   YResolution: 1200
   XCharSize: 8
   YCharSize: 16
   NumberOfPlanes: 1
   BitsPerPixel: 32
   NumberOfBanks: 1
   MemoryModel: 6
   BankSize: 0
   NumberOfImages: 0
   RedMaskSize: 8
   RedFieldPosition: 16
   GreenMaskSize: 8
   GreenFieldPosition: 8
   BlueMaskSize: 8
   BlueFieldPosition: 0
   RsvdMaskSize: 8
   RsvdFieldPosition: 24
   DirectColorModeInfo: 0
   PhysBasePtr: 0xe8000000
   LinBytesPerScanLine: 6400
   BnkNumberOfImagePages: 0
   LinNumberOfImagePages: 0
   LinRedMaskSize: 8
   LinRedFieldPosition: 16
   LinGreenMaskSize: 8
   LinGreenFieldPosition: 8
   LinBlueMaskSize: 8
   LinBlueFieldPosition: 0
   LinRsvdMaskSize: 8
   LinRsvdFieldPosition: 24
   MaxPixelClock: 230000000
Mode: 5c (1920x1440)

... snip ...

(II) I810(0): DELL E207WFP: Using hsync range of 30.00-83.00 kHz
(II) I810(0): DELL E207WFP: Using vrefresh range of 56.00-75.00 Hz
(II) I810(0): Not using mode "1680x1050" (no mode of this name)
(II) I810(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0):  Built-in mode "1024x768"
(**) I810(0):  Built-in mode "800x600"
(**) I810(0):  Built-in mode "640x480"
(II) I810(0): Attempting to use 75.02Hz refresh for mode "1280x1024" (858)
(II) I810(0): Attempting to use 75.08Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "640x480" (850)
```

It looks to me like the video BIOS isn't reporting that it supports that resolution, but "something" (perhaps the monitor itself?) is reporting that it does, in the "Supported additional Video Mode:" section.  I'm not completely clear on how this all works, but apparently the i810 driver only uses resolutions that the BIOS claims to support.  (Interestingly, my coworker has exactly the same hardware and it's working fine under Windows for him).

Anyway, I searched around and found two possible solutions: create a modeline that specifies exactly what the monitor needs, or patch the video card's BIOS.

I tried creating a modeline with gtf, and using only that modeline in xorg.conf.  The monitor says optimal mode is 1680x1050 at 60Hz:

```
baron@kansascity:~$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
```

This modeline was ignored, with similar messages as above in the log, and the monitor fell back to 1280x1024.  I then tried creating a modeline from the output found in the log:

```
(II) I810(0): Supported additional Video Mode:
(II) I810(0): clock: 146.2 MHz   Image Size:  430 x 270 mm
(II) I810(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
(II) I810(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
(II) I810(0): Serial No: 641806A53JXL
(II) I810(0): Ranges: V min: 56  V max: 75 Hz, H min: 30  H max: 83 kHz, PixClock max 150 MHz
```

The modeline I created is as follows:

```
Modeline "1680x1050@60" 146.2 1680 1784 1960 2240 1050 1053 1059 1089
```

I also tried adding -HSync +VSync at the end.

This time the log didn't show the modeline being eliminated with a "Not using mode" message, but the monitor itself refused to display anything.  The monitor went black and the following appeared in bright yellow in the middle of it:

```
1: Analog Input
Cannot Display This Video Mode
Optimum Resolution 1680x1050 60 Hz
```

I then tried creating the Monitor section from edid output:

```
Section "Monitor"
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
        Identifier "DELL E207WFP"
        VendorName "DEL"
        ModelName "DELL E207WFP"
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        HorizSync 30-83
        VertRefresh 56-75
        # Max dot clock (video bandwidth) 150 MHz
        # Block type: 2:0 3:fc
        # DPMS capabilities: Active off:yes  Suspend:yes  Standby:yes

        Mode    "1680x1050"     # vfreq 59.954Hz, hfreq 65.290kHz
                DotClock        146.250000
                HTimings        1680 1784 1960 2240
                VTimings        1050 1053 1059 1089
                Flags   "+HSync" "-VSync"
        EndMode
        # Block type: 2:0 3:ff
        # Block type: 2:0 3:fd
        # Block type: 2:0 3:fc
EndSection
```

This didn't work either.  At this point I read about how to patch the video BIOS with 915resolution.  This causes the video card, which currently reports the following:

```
root@kansascity:~# 915resolution -l
Intel 800/900 Series VBIOS Hack : version 0.5.2

Chipset: 845G
BIOS: TYPE 2
Mode Table Offset: $C0000 + $38a
Mode Table Entries: 18

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1920x1440, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1920x1440, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1920x1440, 32 bits/pixel
```

to report 1680x1050 resolution in modes 3a, 4b and 5a.  The corresponding output shows up in Xorg.0.log of course.  But the monitor complains that it can't display that mode, and at that point I have to reboot the machine to get it working again.

One thing I'm curious about is if it's actually setting a 60Hz refresh rate.  The log output says it "Will use BIOS call 0x5f05 to set refresh rates for CRTs" but later in the output it says "(WW) I810(0): Extended BIOS function 0x5f05 not supported."  I wonder if it's trying 1680x1050 resolution but not the right refresh rate.

I've tried everything I can think of at this point.  Any help is gratefully received.  Thanks in advance!

---

### Post by bps7j on 2006-12-27
Bump.  Anyone?  I've just spent another few hours reading forum posts and trying things.  No matter what I do, I get either a) xorg decides widescreen isn't supported and uses smaller size or b) The monitor itself refuses to display the input it gets.

I was able to verify that the refresh rate is set correctly on other resolutions, so I doubt that is the problem.

---

### Post by evilghost on 2006-12-27
I noticed you created the mode "1680x1050_60.00" and "1680x1050@60.00" however where do you reference this mode in your "Screens" section in xorg.conf?

---

### Post by Stephen47 on 2006-12-27
I was having the same problem with a dell Inspiron E1505. I found that usint this command:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg"
enabled me to have 1680x1050 resolution. However it is only session based bacouse when I reboot I have to run this command again. I haven't found out haow to make the changes permanent. Hope this helps somewhat.

---

### Post by bps7j on 2006-12-28
Thanks to both of you for writing in.  I'll attach my xorg.conf as xorg.txt.  I have hand-written it, and stripped out everything unnecessary to try to eliminate confusion (for example, everything but 24-bit Display subsections).

Right now I only have the one modeline in it, the one from the "Supported additional video mode", because the others clearly weren't working.  This one apparently won't work anymore either (the monitor no longer complains; xorg doesn't try to use it, and skips to 1280x1024 instead.  Rebooting may have changed that, because at one point anyway, xorg was trying to use it and the monitor was saying it couldn't display it).

Stephen47, I know what an md5sum is, but I don't understand why you're doing it.

---

### Post by bps7j on 2006-12-28
I'll attach my Xorg.0.log too... it's too big to attach as plain text, so I've zipped it.

---

### Post by evilghost on 2006-12-28
Why does 915resolution -l only list modes that aren't 16:9 widescreen resolutions?  That's weird...

---

### Post by bps7j on 2006-12-28
> **evilghost said:**
> Why does 915resolution -l only list modes that aren't 16:9 widescreen resolutions?  That's weird...
Because the BIOS on the graphics card only supports those modes.  915resolution's job is to patch the BIOS so the i810 driver, which relies on the BIOS, realizes it's possible to display widescreen.  Unfortunately, in this case when I do that, the monitor itself complains that it can't display whatever input it's getting.

Does anyone know how I can figure out what input the monitor is really getting, which it isn't able to display?

---

### Post by Stephen47 on 2006-12-28
> **bps7j said:**
> Thanks to both of you for writing in.  I'll attach my xorg.conf as xorg.txt.  I have hand-written it, and stripped out everything unnecessary to try to eliminate confusion (for example, everything but 24-bit Display subsections).

Right now I only have the one modeline in it, the one from the "Supported additional video mode", because the others clearly weren't working.  This one apparently won't work anymore either (the monitor no longer complains; xorg doesn't try to use it, and skips to 1280x1024 instead.  Rebooting may have changed that, because at one point anyway, xorg was trying to use it and the monitor was saying it couldn't display it).

Stephen47, I know what an md5sum is, but I don't understand why you're doing it.

I am just following the advice given here:[https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28resolution%29)

---

### Post by diaconal on 2006-12-31
Hi,

I'm spent a few hours yesterday trying to do same thing. I have a 845G with Sceptre X20WG, with native resolution 1680x1050. I've gotten it to the point where I've tried various modelines (unsuccessfully). 

I know the monitor works because I've been able to run it with my laptop at the native resolution. 

I'm vary qurious about this error:

> One thing I'm curious about is if it's actually setting a 60Hz refresh rate. The log output says it "Will use BIOS call 0x5f05 to set refresh rates for CRTs" but later in the output it says "(WW) I810(0): Extended BIOS function 0x5f05 not supported." I wonder if it's trying 1680x1050 resolution but not the right refresh rate.

I have the same error and I wonder if this the real issue. My last resort would be to install Windows on this machine just to test if the 845g is the issue but has anyone gotten anywhere with this?

---

### Post by bps7j on 2006-12-31
> **diaconal said:**
> Hi,

I'm spent a few hours yesterday trying to do same thing. I have a 845G with Sceptre X20WG, with native resolution 1680x1050. I've gotten it to the point where I've tried various modelines (unsuccessfully). 

I know the monitor works because I've been able to run it with my laptop at the native resolution. 

I'm vary qurious about this error:



I have the same error and I wonder if this the real issue. My last resort would be to install Windows on this machine just to test if the 845g is the issue but has anyone gotten anywhere with this?
I'm sure the card is not the issue.  Like I said, my coworker running Windows has no problems on the same hardware.  I think the i810 driver is the problem.

---

### Post by nyvalbanat on 2007-01-09
bps7j: I have the exact same problem with same hardware, except that in 1680x1050 it doesn't blank out and instead it shows the lower-right part of the screen. When I ask it to auto-adjust, it briefly shows (almost) the whole desktop and then zooms back into lower-right corner.
I found this link ([http://bgoglin.free.fr/dimension3000.php](http://bgoglin.free.fr/dimension3000.php)) that you may find interesting, but no solution.
Btw, the same hardware runs out-of-the-box with WinXP.

-Val

---

### Post by nyvalbanat on 2007-01-09
Try messing around with the monitor's Image Settings and then auto-adjust. I finally got it to work, although the fonts are not as clear for me now - probably some anti-aliasing setting somewhere...
-V

---

### Post by andrewjorgensen on 2007-01-24
I managed to solve this problem for myself by installing xserver-xorg-video-intel (universe) which appears to be a build of the experimental modesetting branch of the driver.  This obsoletes 915resolution.  Change the driver in xorg.conf to intel (from i810) after installation.

---

### Post by nyvalbanat on 2007-01-29
andrewjorgensen, you are THE MAN!!! This driver totally works.
Thanks a bunch!
-Val

---

### Post by dotman on 2007-03-07
AH big props to andrew! Worked on an Intel 845G chipset with a Dell 20" widescreen, its a E207wfp. not sure if people with the 2007wfp are having the same problem but they may want to try this.

---

### Post by dotman on 2007-03-07
***oops***

---

### Post by ramjet_1953 on 2007-03-08
Try this link.

[http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution](http://www.ubuntuforums.org/showthread.php?t=351647&highlight=915resolution)

Regards,
Roger :cool:

---

### Post by gurgle on 2007-03-27
> **andrewjorgensen said:**
> I managed to solve this problem for myself by installing xserver-xorg-video-intel (universe) which appears to be a build of the experimental modesetting branch of the driver.  This obsoletes 915resolution.  Change the driver in xorg.conf to intel (from i810) after installation.

this fixed my issues on my Dell GX280, thanks.

---

### Post by Bobtheknight on 2007-04-08
Hey sorry to revive this thread if it's dead for a while.  I can not find xserver-xorg-video-intel under universe :(

I can download the deb package from packages.debian.org, but it says dependency unsatisfiable: xserver-xorg-core.

Bobtheknight

---

### Post by vanderwaal on 2007-07-05
Hey All,

I don't post on here much, but instead mostly read. Finally, though, I found a thread that I could contribute to! I had this very problem on my new Dell Dimension C521 desktop with a Dell E207WFP monitor (widescreen, flat panel). What fixed it wasn't fixing an Intel chipset (although I'm sure that would work if you had an intel chipset and that was indeed the problem). I have a NVidia chipset (with and AMD64 processor). What helped was this:

nvidia-glx-new at packages.ubuntu.com. Apparently you need this installed, and Dell too has forgotten to include this package in many of their ubuntu shipments. Widescreen monitors can't get the resolution they need without this package (for some reason, don't ask me why). So don't bother editing you xorg.conf file when all you need is this package and a reboot of the X server :-)

-William

---

### Post by apoth on 2007-07-06
> **andrewjorgensen said:**
> I managed to solve this problem for myself by installing xserver-xorg-video-intel (universe) which appears to be a build of the experimental modesetting branch of the driver.  This obsoletes 915resolution.  Change the driver in xorg.conf to intel (from i810) after installation.

Brilliant, thank you :)

---

### Post by sigvartb on 2007-07-13
Thank you, this fixed my problem with Dell Optiplex GX620 with built-in intel 82945 graphics. Can now use the wide Dell E228WFP with Ubuntu 7.04

---

