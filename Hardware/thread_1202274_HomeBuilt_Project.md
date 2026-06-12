---
title: "HomeBuilt Project"
date: 2009-07-02
forum: Hardware
---

### Post by VaioPengiun on 2009-07-02
Well, I've been bit by the Linux bug so here's a thread to share my triumphs with my home built tower of power (not really).

Specs:
ASRock 939Dual-VSTA w/AM2CPU Board
AMD Athlon 64 X2 5200+ Dual core
4GB DDR2 800
NVidia 9800GT (512MB)
SB Audigy 2

Displays:
20" Samsung SyncMaster 205BW
19" HANNS-G HW191D

[B]First Issue: 1440x900 Max Resolution on SyncMaster (native = 1680x1050)
[/B]I had the same problem when running XP, but switching to an analogue input fixed it there---> not the case with NVidia Linux drivers.

It turns out the Samsung SyncMaster refurbished monitor I have was shipped out with the wrong EDID information. After running *ddcprobe *I got to see what the autodetection was seeing:
```
kobbler@BigKobbler:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVIDIA
vendor: NVIDIA Corporation
product: G92 Board - 03930004 Chip Rev
memory: 14336kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
edid: 
edid: 1 3
id: 01d3
eisa: SAM01d3
serial: 48413230
manufacture: 28 2006
input: composite sync, sync on green, analog signal.
screensize: 41 26
gamma: 2.200000
dpms: RGB, active off, no suspend, no standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1440x1440@60
ctiming: 1440x1440@75
ctiming: 1280x1024@60
ctiming: 1280x960@60
ctiming: 1152x864@75
**dtiming: 1440x900@69**
monitorrange: 30-81, 56-75
monitorname: SyncMaster
monitorserial: HVFL702001

```Luckily NVidia has a couple neat features that allow you to save the EDID info to a binary file and allow you too use any EDID binary file for the EDID info in your *xorg.conf* file (rather than using the garbage stored in the hardware).

In the *nvidia-settings *GUI-->GPU section-->(monitor in question)CRT-0 press the [Acquire EDID...] button and save it.
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/Screenshot-NVIDIAXServerSettings.png[/IMG]

I then used *ghex* editor (the file is a binary file and requires a binary editor) and the calculator (for decimal/hexidecimal conversion) to make the necessary changes.  The following is the original file (stating **1440x900** max resolution):
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/Screenshot-edidbin-GHex.png[/IMG]

The **Horizontal screen size** (in pixels) is stored in Offset bits 38 and (first bit of)3A:

offset 38 = **A0**     offset 3A = **5**1

(values in bold apply to horizontal value as follows: 0x**5A0**)  Do the conversion using your programmers calculator and you get a decimal value of **1440**.

Plug the desired value of **1680 **into handy calculator and convert to get 0x**690** and enter the hex values as follows:

offset 38 = **90**     offset 3A = **6**1


The **Vertical screen size** (in pixels) is stored in Offset bits 3B and (first bit of)3D:

offset 3B = **84**     offset 3D = **3**0

(values in bold apply to vertical value as follows: 0x**384**)  Do the conversion using your programmers calculator and you get a decimal value of **900**.

Plug the desired value of **1050 **into your handy calculator and convert to get 0x**41A** and enter the hex values as follows:

offset 38 = **1A**     offset 3A = **4**0

My final looks like this (with **1680x1050** native):
[IMG]http://i918.photobucket.com/albums/ad26/kobbler248/Screenshot-edidbin-GHex-1.png[/IMG]






With that done and saved, I added the following line to the *xorg.conf* file
```
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GT"
   ** Option       "CustomEDID" "CRT-0:/home/kobbler/edid.bin"**
EndSection
```Logged out and back in and... Voila!  Full graphics capability on the Samsung


I hope it's not too confusing, but I liked the idea better than adding 15 - 25 lines to my xorg.conf file.  And again, I hope this helps!

---

### Post by mikehattingh on 2009-12-25
Thanks VaioPengiun this was a great help in getting my viewsonic 1080p tv to finally display at full res.

Two things though,
(typo) the offsets for the vertical pixel count are 3B,3D

And it will be necessary to update the checksum located at offset 127 0h7f: This byte should be programmed such that the sum of all 128 bytes equals XX00h.

---

