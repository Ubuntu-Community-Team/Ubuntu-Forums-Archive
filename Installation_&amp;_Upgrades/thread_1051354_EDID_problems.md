---
title: "EDID problems"
date: 2009-01-26
forum: Installation &amp; Upgrades
---

### Post by purrcy on 2009-01-26
Hi, I just installed Ubuntu 8.10, installed the updates, and rewrote the xorg.conf.  Everything seems to work fine, but there are some warnings in the Xorg.0.log that says that, "The EDID read for display device CRT-0 is invalid," and,"Unable to get display device CRT-0's EDID; cannot compute DPI."   The current DPI is set to 75 and I would like to set it to 120.

I don't know what to do about the EDID, and I can't understand anything that I have read about it on the net.  Can someone tell me in plain English what to do?

---

### Post by purrcy on 2009-01-27
OK, let me kick this off.  My dpi was stuck on 75x75, so I added the last two lines to the Monitor Section of xorg.conf: 

Section "Monitor" 
    Identifier     "Configured Monitor"     
VendorName         "Samsung" 
    ModelName         "Samsung SyncMaster 900NF" 
    HorizSync         30-110     
VertRefresh     50-160 
    Option         "UseEDIDDpi"     "false"     
Option         "Dpi"         "120x120" 
EndSection  

My dpi is now set to 120x120.  But I still have the original problem with my EDID.  Any suggestions?

---

### Post by purrcy on 2009-01-27
OK. I installed ddcprobe and was able to bet this information:

ron@purrcy:~$ sudo ddcprobe
vbe: VESA 3.0 detected.
oem: NVidia
vendor: NVidia Corporation
product: NV20 (GeForce3) Board Chip Rev A3
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 1280x1024x16
mode: 1280x1024x256
mode: 80x60 (text)
mode: 132x25 (text)
mode: 132x43 (text)
mode: 132x50 (text)
mode: 132x60 (text)
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x64k
edid: &#65533;??-L&#65533;891GP
                       $e&#65533;&#65533;&#65533;WI&#65533;&HL&#65533;&#65533;&#65533;&#65533;&#65533;aY&#65533;Y&#65533;@&#65533;=
edid: 1 2
id: 38d9
eisa: SAM38d9
serial: 50473139
manufacture: 30 2001
input: separate sync, composite sync, sync on green, digital signal.
screensize: 36 27
gamma: 2.010000
dpms: RGB, active off, suspend, standby
timing: 720x400@70 Hz (VGA 640x400, IBM)
timing: 720x400@88 Hz (XGA2)
timing: 640x480@60 Hz (VGA)
timing: 640x480@67 Hz (Mac II, Apple)
timing: 640x480@72 Hz (VESA)
timing: 640x480@75 Hz (VESA)
timing: 800x600@56 Hz (VESA)
timing: 800x600@60 Hz (VESA)
timing: 800x600@72 Hz (VESA)
timing: 800x600@75 Hz (VESA)
timing: 832x624@75 Hz (Mac II)
timing: 1024x768@87 Hz Interlaced (8514A)
timing: 1024x768@60 Hz (VESA)
timing: 1024x768@70 Hz (VESA)
timing: 1024x768@75 Hz (VESA)
timing: 1280x1024@75 (VESA)
ctiming: 1280x1024@85
ctiming: 1024x768@85
ctiming: 1600x1200@85
ctiming: 2048x1536@60
dtiming: 1280x1024@99
monitorrange: 30-110, 50-160
monitorname: S/M 900NF
monitorserial: H2HR701342
ron@purrcy:~$ 

Is this the file I need to establish the EEIE?  If so, how do I put this into my xorg.conf?

You know, it seems to me that if the Ubuntu developers had inlcuded this package in the install they could have configured the xorg.conf!

---

