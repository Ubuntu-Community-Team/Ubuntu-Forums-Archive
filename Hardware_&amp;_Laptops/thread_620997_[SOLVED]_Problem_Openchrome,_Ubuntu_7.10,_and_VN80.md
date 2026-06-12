---
title: "[SOLVED] Problem: Openchrome, Ubuntu 7.10, and VN800"
date: 2007-11-23
forum: Hardware &amp; Laptops
---

### Post by coady on 2007-11-23
I have installed the openchrome driver in Debian Etch, Fedora 8, and Ubuntu 7.10. In the case of the Debian and Fedora the driver is recognised, X-server and GDM load without trouble. The driver is being loaded:```
grep openchrome /var/log/Xorg.0.log

(II) LoadModule: "openchrome"
```In the case of Ubuntu 7.10 the openchrome driver is loaded but 'X-server' fails and GDM will not load. This has been the case with both upgrades and fresh installs of Ubuntu 7.10. The X-server defaults to 'xorg.conf.failsafe'.

Can someone please help me with this...?

I am no expert, but on comparing the 'Xorg.0.log' files in both Debian Etch and Ubuntu 7.10 the only lines I can find that look suspect are the following:

From Ubuntu:```
(II) VIA(0): Generic Monitor: Using default hsync range of 28.00-33.00 kHz
(II) VIA(0): Generic Monitor: Using default vrefresh range of 43.00-72.00 Hz
(II) VIA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using built-in mode "1280x768" (width too large for virtual size)
(II) VIA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(--) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Built-in mode "1024x768"
(**) VIA(0): *Built-in mode "800x600"
(**) VIA(0): *Built-in mode "640x480": 0.0 MHz, 31500.5 kHz, 60.5 Hz
(II) VIA(0): Modeline "640x480"    0.00  640 0 0 0  480 0 0 0
(++) VIA(0): DPI set to (96, 96)
```
From Debian:```
(II) VIA(0): Generic Monitor: Using default hsync range of 31.50-37.90 kHz
(II) VIA(0): Generic Monitor: Using default vrefresh range of 50.00-70.00 Hz
(II) VIA(0): Not using built-in mode "1600x1200" (width too large for virtual size)
(II) VIA(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(II) VIA(0): Not using built-in mode "1280x768" (width too large for virtual size)
(II) VIA(0): Attempting to use 60Hz refresh for mode "800x600" (115)
(II) VIA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(--) VIA(0): Virtual size is 1024x768 (pitch 1024)
(**) VIA(0): *Built-in mode "1024x768"
(**) VIA(0): *Built-in mode "800x600": 0.0 MHz, 37879.3 kHz, 60.8 Hz
(II) VIA(0): Modeline "800x600"    0.00  800 0 0 0  600 0 0 0
(**) VIA(0): *Built-in mode "640x480": 0.0 MHz, 31469.2 kHz, 60.4 Hz
(II) VIA(0): Modeline "640x480"    0.00  640 0 0 0  480 0 0 0
(**) VIA(0):  Built-in mode "720x576"
(**) VIA(0):  Built-in mode "720x540"
(**) VIA(0):  Built-in mode "800x480"
(**) VIA(0):  Built-in mode "720x480"
(==) VIA(0): DPI set to (100, 100)
```
Thanks for any help.

Attached:
Ubuntu 'xorg.conf'
Ubuntu 'Xorg.0.log'
Debian 'xorg.conf'
Debian 'Xorg.0.log'

---

### Post by coady on 2007-11-23
Looking at the compared sections from the 'Xorg.0.log' files (above) it appears that the reported Hsync and Vsync from the **same monitor** are not the same. My guess is the monitor doesn't advertise them properly and then X falls back to the defaults which are not the same from one distro to the other. Does anyone know how to force the monitor's Hsync and Vsync to definite values (e.g. those values given by the Debian section above)?

---

### Post by coady on 2007-11-24
I have resolved this issue with the kind help of the developers of openchrome (thanks to Xavier :)). I finally had to manually force the monitor settings. I don't know if the problem was with the values being incorrectly reported by the LCD panel or if for some reason Ubuntu 7.10 was misrecognizing the panel, but 'X' kept falling back to a failsafe 'xorg.conf' where the monitor values were incorrect. I persisted in trying to fix it and adding the following to 'xorg.conf' seems to have solved the problem (I added the commented lines, thinking ahead of all options, but I did not finally use them):```
Section "Monitor"
     Identifier   "Generic Monitor"
     **HorizSync    31-48**
     **ModelName    "1024X768@60HZ"**
     Option       "DPMS"
     **VertRefresh  50-60**
     # V-freq: 60.00 Hz  // h-freq: 47.80 KHz
     # Modeline  "1024x768" 60.80  1024 1056 1128 1272   768  768  770  796
EndSection
```Note that there seemed to be a problem when the 'HorizSync' and 'VertRefresh' inputs were wrapped in quotes (i.e. "") as shown in the many examples I looked at. I am not sure if this is an important issue but it worked by leaving the quotes off these inputs. Anyway, it seems to be solved for now.

I also found that once I could get the X-server running and boot into a graphical desktop that I have a further problem with the screen going grey (I know of this problem via a post to the openchrome list, relating to a Fedora 8 installation). Following the advice there I added the following to the 'xorg.conf':```
Section "Device"
   Identifier "Generic Video Card"
   Driver  "openchrome"
   BusID  "PCI:1:0:0"
   Option  "SWcursor" "true"
   **Option  "EnableAGPDMA" "off"**
EndSection
```
The devs at openchrome have pointed out that this is only a temporary work around. Some helpful links I used when resolving this are:
[LIST][HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")[/LIST]
[LIST][Testing  changes in xorg without restarting GDM]("http://ubuntuforums.org/showpost.php?p=679706&postcount=23")[/LIST]

I hope this helps some people.
coady

---

