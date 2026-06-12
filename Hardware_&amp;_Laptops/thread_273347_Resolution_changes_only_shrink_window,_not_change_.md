---
title: "Resolution changes only shrink window, not change resolution"
date: 2006-10-07
forum: Hardware &amp; Laptops
---

### Post by skyemoor on 2006-10-07
Dell Latitude C810
GeForce2 Go
Dell 1907FPc flat screen display
Dapper 6.06

Background: Ubuntu comes up only in 1600x1200 on my laptop display, which is unreadable with my eyesight. 

Problem: Attempts to change the xorg.conf file to accept other screen sizes only shrink the window, not reduce resolution. Several attempts using techniques found herein have no yielded success. My flat screen display can only show 1280x1024, so that's what I set my resolution to. The laptop image shrinks, instead of shows at lower resolution. When I hook up my flat screen display, it gives the error:

"1. Analog input. 1280x1024 60 Hz resolution optimal"
Oddly enough, Ubuntu startup displays show up, all the way up to showing gnome (I'm assuming).

I tried;
[https://help.ubuntu.com/community/Fi...esolutionHowto](https://help.ubuntu.com/community/Fi...esolutionHowto)
Result: Had to restore my x11.conf file

Looked at other help pages, but the only one I saw had a list of legacy GeForce2 display adapters, though none were mine, so I couldn't tell if I should use the xgl or legacy driver.

Here's a smattering of my xorg.conf;

Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 Go]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-80
VertRefresh 43-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "NVIDIA Corporation NV11 [GeForce2 Go]"
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display"
Depth 1
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 4
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 8
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 15
Modes "1600x1200"
EndSubSection
SubSection "Display"
Depth 16
Modes "1280x1024" "1600x1200"
EndSubSection
SubSection "Display"
Depth 24
Modes "1280x1024" "1600x1200"
EndSubSection

Originally, only 1600x1200 was listed. I added 1280x1024 as shown above, but now when the display resolves to gnome, the window I can see things in is slightly smaller than full size, and I have to reduce my screen resolution to 1280x1024 in order to see the outer edges of the windows (it's like looking at a picture where the borders cover up the outer edge).

---

### Post by K.Mandla on 2006-10-08
Is there a BIOS option for screen scaling? I had an M170 that had an option in the BIOS to stretch a resolution to fit the monitor, or to display it centered (or scale it, I think). 

Anyway, an idea. :|

---

### Post by skyemoor on 2006-10-08
The Dell support site forum had a hint to use Fn-F7, which shifted my output to full screen resolution after bootup.  That still doesn't work for the external LCD flat screen monitor, however, which still gives the same error message about not displaying anything greater than 1280x1024.

I've considered a bios change, and found an update on the Dell site (A12-C810.EXE).  However, it has only been tested on Windows platforms, though it does mention a fix to external LCD displays.  It also says that I must update my nVidia driver at the same time.
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R57194&SystemID=LAT_PNT_P3C_C810&os=LNUX&osl=en&deviceid=1330&devlib=0&typecnt=1&vercnt=9&formatcnt=4&libid=1&fileid=68408](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R57194&SystemID=LAT_PNT_P3C_C810&os=LNUX&osl=en&deviceid=1330&devlib=0&typecnt=1&vercnt=9&formatcnt=4&libid=1&fileid=68408)

The nVidia site lists a linux update for IA32 or IA64, and I assume I choose the former.  They also distinguish between Latest Version and Latest Legacy GPU Version, where I assume with a GeForce2 Go I choose the latter.
[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

There's a section on Linux nForce Drivers, but with a GeForce2 card, it doesn't seem applicable;
[http://www.nvidia.com/object/linux_nforce_1.11.html](http://www.nvidia.com/object/linux_nforce_1.11.html)

Should I attempt a BIOS update with the above mentioned A12-C810.EXE and if so, use the nViadia IA32 Legacy Version Update?

---

### Post by skyemoor on 2006-10-09
Problem solved!  The monitor still displays "No Signal" after the initial screen splash, and during login (!), but around the time gnome loads, the display reappears and works fine.  One needs to make sure that they get a beep/click when login is prompted (or simply assume the amount of time that passes).

Not perfect, but it beats cracking into video drivers and a host of other innards, at least for this noob.

---

