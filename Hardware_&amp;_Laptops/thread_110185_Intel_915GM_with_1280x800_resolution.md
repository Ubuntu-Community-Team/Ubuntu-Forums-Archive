---
title: "Intel 915GM with 1280x800 resolution"
date: 2005-12-30
forum: Hardware &amp; Laptops
---

### Post by simohell on 2005-12-30
I have got a new laptop with which the only Ubuntu (5.10)/Linux problem so far is the screen resolution. The computer is none of the big brands, but a "D-code M30" which is sold as far as I know only in Finland. It has Intel 915GM and 1280x800 TFT screen.

The problem I have is that I get a stretched 1024x768 resolution only. I have gone through all the 915 guides and threads I could find. None helped so far. (I could even live with having 1024x768 it the propotions went right, like leaving part of the screen blank like some of the oldfashioned laptops used to do.)

Also my X wont restart at ctrl-alt-backspace (or wont display anything if it does).

1. I installed and configured 915resolution (Debian version)
Tried it with a few configurations - with and without depth=24

```
Intel 800/900 Series VBIOS Hack : version 0.5

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x800, 8 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x800, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x800, 32 bits/pixel

```

2. Ran dpkg-reconfigure a few times 

3. Edited my xorg.conf with a lot of different options
- tried a few diffrent modelines
- tried it with vesa-drivers
- tried it with some different refresh rates (currently keeping the one Knoppix identified) and ended up getting listed the standard low resolution options from 1024x768 to 640x480 (which I didn't get at clean install, I only go 1024x786 although at installation my xorg.conf had 1280x768)


```

Section "Device"
        Identifier      "Intel 915GM"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        128000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "LCD 1280x800"
        Option          "DPMS"
        HorizSync       28-96
        VertRefresh     50-75
        Modeline        "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel 915GM"
        Monitor         "LCD 1280x800"
        DefaultDepth    24
#       SubSection "Display"
#               Depth           1
#               Modes           "1280x800"
#       EndSubSection
#       SubSection "Display"
#               Depth           4
#               Modes           "1280x800"
#       EndSubSection
#       SubSection "Display"
#               Depth           8
#               Modes           "1280x800"
#       EndSubSection
#       SubSection "Display"
#               Depth           15
#               Modes           "1280x800"
#       EndSubSection
#       SubSection "Display"
#               Depth           16
#               Modes           "1280x800"
#       EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x800"
        EndSubSection
EndSection
```

4. I tried if Knoppix (3.8.2) would ID my screen or if it would accept 1280x800 mode as a parameter. It did accept the 1280x800 for the configuration but showed 1024x768 streched to fill the display.

- - -

Here is also my output from ddcprobe, which at least gives me the wrong amount of memory (I've got 512MB and 128MB is reserved by the graphics adapter):

```
vbe: VESA 3.0 detected.
oem: Intel(r)915GM/910ML/915MS Graphics Chip Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(r)915GM/910ML/915MS Graphics Controller Hardware Version 0.0
memory: 16064kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edidfail

```

I will add my Xorg.0.log a bit later...

[edited]

I added the log as an attachement (gzip)

It gives quite a few hints about the problems, but I'm no that good in figuring out how to fix them. I'd appriciate the help of an expert.

I suppose I'll need to check if the vendors 1280x800 resolution REALLY is 1280x768 and there seems to be something strange with the graphics memory as well.

---

### Post by simohell on 2005-12-30
Nope--Didn't help changing the resolution to 1280x768

I'd expect this is the key point in Xorg.0.log:

```
(II) I810(0): Not using mode "1280x768" (no mode of this name)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0):  Built-in mode "1024x768"

```

Also just before that it says:
```

Mode: 3c (0x0)
        ModeAttributes: 0x0
        WinAAttributes: 0x0
etc.

```

Meaning probably that it does not find any mode 1280x768...
although "sudo 915resolution -l" gives me such a mode:
```
Intel 800/900 Series VBIOS Hack : version 0.5

Chipset: 915GM
BIOS: TYPE 1
Mode Table Offset: $C0000 + $269
Mode Table Entries: 36

Mode 30 : 640x480, 8 bits/pixel
Mode 32 : 800x600, 8 bits/pixel
Mode 34 : 1024x768, 8 bits/pixel
Mode 38 : 1280x1024, 8 bits/pixel
Mode 3a : 1600x1200, 8 bits/pixel
Mode 3c : 1280x768, 24 bits/pixel
Mode 41 : 640x480, 16 bits/pixel
Mode 43 : 800x600, 16 bits/pixel
Mode 45 : 1024x768, 16 bits/pixel
Mode 49 : 1280x1024, 16 bits/pixel
Mode 4b : 1600x1200, 16 bits/pixel
Mode 4d : 1280x768, 16 bits/pixel
Mode 50 : 640x480, 32 bits/pixel
Mode 52 : 800x600, 32 bits/pixel
Mode 54 : 1024x768, 32 bits/pixel
Mode 58 : 1280x1024, 32 bits/pixel
Mode 5a : 1600x1200, 32 bits/pixel
Mode 5c : 1280x768, 32 bits/pixel

```

So, how to make it visible to X?

---

### Post by simohell on 2005-12-30
I managed to fix it eventually based on a comment on google's 915resolution pages.

One has to set all the low resolutions (the ones I can access) to the resolution I want: that is at the moment 1280x768. (and I will go and talk to the vendor about this)

Since I didn't want to mess with my /etc/defaults/915resolution, what I did was I wrote a srcipt to /etc/init.d:
```
# !/bin/sh

915resolution 30 1280 768
915resolution 32 1280 768
915resolution 34 1280 768
915resolution 38 1280 768
915resolution 3a 1280 768
915resolution 3c 1280 768

```

(I'm not sure if I even actually need the last 3 lines, I'll test that later)

And "sudo update-rc.d 915res.sh start 20 S ."

...and voilà

---

### Post by simohell on 2005-12-30
(my openGL rendering however is since "reverting to (slow) indirect rendering" but I don't really use 3D -- so I don't care. If someone does know a solution for it let me know, though.)

```
ERROR!  sizeof(I830DRIRec) does not match passed size from device driver
libGL warning: 3D driver returned no fbconfigs.
libGL error: InitDriver failed
libGL error: reverting to (slow) indirect rendering
1149 frames in 5.4 seconds = 213.904 FPS
1440 frames in 5.4 seconds = 264.487 FPS
1440 frames in 5.4 seconds = 264.658 FPS
1440 frames in 5.4 seconds = 264.776 FPS

```

It is still faster than my former ATI Radeon Mobility U1 (IGP 320).

---

### Post by simohell on 2005-12-31
Got this working as well by now. I swapped back to Breezy's i810 driver instead of intel's version. Also I added to my xorg.conf

```
Load "drm"
```

Now I'm back to 826k FPS

---

### Post by er-ku on 2006-01-01
> memory: 16064kb

I think this is the reason for your problems. IMHO, you should have reserved more shared RAM for video purposes in BIOS.

---

### Post by iNerdSure on 2006-01-13
[QUOTE=er-ku]I think this is the reason for your problems. IMHO, you should have reserved more shared RAM for video purposes in BIOS.[/QUOTE]
Er-ku, how do you achieve the 1280 x 800 resolution on the Acer 4061? I have only partial success, as each time I boot up it reverts back to 1024 x 768. I need to log-out and log-in again (not reboot) to get the display on 1280 x 800.

I believe there must be a more efficient way, such that when booting up it goes directly into 1280 x 800 resolution. :confused:

---

### Post by simohell on 2006-01-20
[QUOTE=er-ku]I think this is the reason for your problems. IMHO, you should have reserved more shared RAM for video purposes in BIOS.[/QUOTE]

I never had only 16MB shared RAM. The output where it says so is false, and apparrently prints out the minimim. (something I probably should report to the guy who wrote the software, actually)

I recon the 915GM uses dynamic memory allocation. If you would have read the Xorg.0.log you would have seen that in my case memory allocated varied between 64MB and my current 128MB. This can be chosen easily in xorg.conf file.

```
Section "Device"
        Identifier      "Intel GMA 900"
        Driver          "i810"
        BusID           "PCI:0:2:0"
        VideoRam        131072
        Option          "MonitorLayout" "CRT,LFP"
        Screen          0
EndSection

```

So, the amount of memory is definately not related to the issue.

Anyway, for the past 2 weeks I have been a perfectly happy user on 3.9 Megapixels of Gnome desktop (1280x768 + 1600x1200 external TFT)

My current issue is only to choose between several different Xorg.conf layouts in a easy way. Now I have a few I swap using bash-scripts.

---

### Post by darm on 2006-01-26
*have gone through all the 915 guides and threads I could find.*

Were there many? Were they any good? Could you share some of the most useful links?

---

### Post by kingsidy on 2006-01-26
i had the exact same problem on my ubuntu install. i used the 855resolution.deb package to fix it. After i install it and set the resolution, i reconfigure X and i remember making a change on the boot order so that the 855 resolution starts before x or something like that.

---

### Post by darm on 2006-01-26
does that make graphics acceleration work as well?

---

### Post by simohell on 2006-02-10
[QUOTE=darm]*have gone through all the 915 guides and threads I could find.*

Were there many? Were they any good? Could you share some of the most useful links?[/QUOTE]

Well, I just searched for WXGA and 915 threads, and they didn't help much. I got the clue how to use 915resolution, but for me I got the final solution from googles 915resolution forum.

---

### Post by simohell on 2006-02-10
[QUOTE=darm]does that make graphics acceleration work as well?[/QUOTE]

This solution gave me a bit more than 800.000 FPS in glxgears, and direct rendering is enabled. I don't know if it is possible to get more power out of it and for me this is enough.

---

