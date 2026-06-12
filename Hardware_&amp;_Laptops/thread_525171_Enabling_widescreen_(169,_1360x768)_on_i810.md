---
title: "Enabling widescreen (16:9, 1360x768) on i810"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by Paradoxdruid on 2007-08-14
My little first-edition Koala mini from System76 has been serving great as my media hub for quite some time now. Situations change, however: I finally bought a new LCD TV (a Vizio vx37l 37 in LCD TV), and I'm having trouble setting the Koala to a widescreen resolution so that everything isn't squashed onscreen.

Right now, it's supporting 1280x1024 at 60 Hz just fine on the TV, but it won't output a signal at 1280x768 (a suggestion from the Ubuntu forums archive) or 1360x768 or 1366x768.

The system is using the i810 video driver, and is connected via VGA cable.

Any ideas of resolutions / video modelines / something else that could help me get a widescreen picture?

Here's the relevant xorg.conf sections:
> 
Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "i810"
BusID "PCI:0:2:0"
EndSection

Section "Monitor"
Identifier "Vizio VX37L"
Option "DPMS"
HorizSync 30-65
VertRefresh 30-60
EndSection

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Monitor "Vizio VX37L"
DefaultDepth 16
SubSection "Display"
Depth 16
Modes "1280x1024" "1280x768" "1024x768" "800x600" "640x480"
EndSubSection
EndSection


I've run dpkg-reconfigure xserver-xorg over a dozen times, trying different settings. It never offers widescreen geometries (it's apparently an i810 driver issue).

So I followed some advice from the Ubuntu Wiki and installed xserver-xorg-video-intel , which replaces the i810 driver with a newer, intel one. This still didn't offer widescreen modes on xserver reconfiguration, but it sent not usable signal to the monitor. (The Xorg log file showed the intel driver was sending signals to either path A (VGA port) or path B (S-video port), and it had set the X signal to path none. I have no idea how to force the intel driver to actually send a signal.)

Reinstalling the i810 driver, I could at least get the display working. It actually works to send 1024x768 at 16 bits (or 1280x1024, which it must be rescaling in the TV) and get a crisp but stretched picture. I found a TV mode which centers it instead of stretching it, so I can get good resolution-- but only 4:3 ratio.

I still want full 16:9 ratio for the screen, so I tried installing the 915resolution package and manually changing the Video BIOS to offer 1360x768-- it made the driver (from the Xorg log) not find a usable mode and shutdown.

So... I'm out of options. I think the solution lies in installing the xserver-xorg-video-intel package, but I can't get it to send signal correctly. Maybe I need to add a modeline or a setting to force a certain output in my Xorg.conf


Any ideas?  Thanks!

---

### Post by ramjet_1953 on 2007-08-14
Follow this link, and all will be revealed:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_Correct_the_Graphics_Resolution_.28Intel.29)


Regards,
Roger :cool:

---

### Post by Paradoxdruid on 2007-08-14
Thanks for the advice, Roger.  My post was fairly long, so I'm sure it was easy to miss--  but I already tried both the steps that page recommends (915resolution and xserver-xorg-video-intel).  The new driver doesn't work at all, and 915resolution doesn't enable any widescreen modes.

Looking over my X log (which I've attached), at one point it says something like "1360x768 mode not used (too large for virtual size)".  Would manually setting the virtual size larger help solve anything?

Thanks for any further ideas.

---

### Post by Paradoxdruid on 2007-08-14
Diving further into my Xorg log, I see this section at the beginning:
> (II) I810(0): Display Info: CRT: attached: TRUE, present: TRUE, size: (720,400)
(II) I810(0): Display Info: TV: attached: FALSE, present: TRUE, size: (1024,768)
(II) I810(0): Display Info: DFP (digital flat panel): attached: FALSE, present:
TRUE, size: (1366,768)

So it seems that it does see the LCD TV (which has a native resolution of 1366x768).

Much further down, we see the section I referred to in my last post:
> (II) I810(0): Generic Monitor: Using hsync range of 30.00-65.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 50.00-75.00 Hz
(II) I810(0): Not using built-in mode "1360x768" (width too large for virtual si
ze)
(II) I810(0): Not using built-in mode "1360x768" (width too large for virtual si
ze)
(II) I810(0): Increasing the scanline pitch to allow tiling mode (1280 -> 2048).
(--) I810(0): Virtual size is 1280x1024 (pitch 2048)
(**) I810(0): *Built-in mode "1280x1024"
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 60.02Hz refresh for mode "1280x1024" (849)
(II) I810(0): Attempting to use 75.03Hz refresh for mode "1024x768" (845)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "800x600" (843)
(II) I810(0): Attempting to use 75.00Hz refresh for mode "640x480" (841)
(==) I810(0): DPI set to (75, 75)


Looking at the xorg.conf manual page, it says that under the Display Section, I should be able to set Virtual to control the virtual size, but when I add it, X fails to start and the error log says that Virtual is not a recognized option.

Any ideas would help--  thanks!

---

### Post by Paradoxdruid on 2007-08-14
Googling further, I found someone [here]("http://www.nvnews.net/vbulletin/showthread.php?t=58062") with a similar problem, and he found that setting Virtual size did nothing...  but specifying a Modeline in his Xorg.conf worked.  I guess I need to try that when I get home tonight.  But I'd love to actually here some suggestions, if anyone has any.

---

