---
title: "ubuntu slow on thinkpad t41"
date: 2009-04-28
forum: Hardware
---

### Post by jan.naef on 2009-04-28
hi,

i have a thinkpad t41 and use ubuntu 9.04 (recently upgraded from 8.10).

Intel(R) Pentium(R) M processor 1600MHz
widh: 32 bits
Radeon Mobility M7 LW [Radeon Mobility 7500]
IC25N080ATMR04-0 80GB 4200RPM 2.5" ATA IDE HDD
System memory size: 1002MiB

the performance is extremely slow (in both 8.10 and 9.04) as compared to windows xp. it is unuseably slow to switch between windows and tabs, scroll, create files and folders or type an address in firefox.

i tried adding Option "AccelMethod" "XAA" to /etc/X11/xorg.conf, as suggested elsewhere in this forum ([http://www.uluga.ubuntuforums.org/showthread.php?p=7148225](http://www.uluga.ubuntuforums.org/showthread.php?p=7148225)), however this had no effect on my laptop.

what can i do? any help is highly appreciated.

---

### Post by teclis on 2009-04-30
I have the same Laptop and same problem.

Adding XAA helped me:

Section "Device"
	Identifier	"Configured Video Device"
	Driver "ati"
	Option "DynamicClocks" "on"
	Option "mtrr" "on"
	Option "DesktopSetup" "Single"
	Option "ScreenOverlap" "0"
	Option "VideoOverlay" "on"
	Option "OpenGLOverlay" "off"
	Option "Stereo" "off"
	Option "StereoSyncEnable" "1"
	Option "FSAAEnable" "no"
	Option "FSAAScale" "1"
	Option "FSAADisableGamma" "no"
	Option "FSAACustomizeMSPos" "no"
	Option "UseFastTLS" "0"
	Option "BlockSignalsOnLock" "on"
        Option          "XAANoOffscreenPixmaps"
	Option "AccelMethod" "XAA"
EndSection

---

### Post by akom on 2009-06-09
Made a huge difference for my suddenly slow T42.
The slowness began sometime after the 9.04 upgrade.

My xorg.conf (lines I took from you are in red)

Section "Device"
Identifier "Radeon Mobility M7"
Driver "radeon"
BusID "PCI:1:0:0"
Option "ColorTiling" "false"
[COLOR="Red"]Option "XAANoOffscreenPixmaps"
Option "AccelMethod" "XAA"[/COLOR]
Option "Monitor-LVDS" "LVDS Monitor"
Option "Monitor-VGA-0" "VGA-0 Monitor"
Option "Monitor-DVI-0" "DVI-0 Monitor"
EndSection

Thanks!

---

### Post by boublik on 2009-10-08
I have the T41 with 1.4 Ghz and 1.2Gib memory and it runs like a horse, or maybe it's just a fresh installation.

---

### Post by Dorlack on 2009-10-27
I hope we can get a reply back to this! I have the same issue... 9.04 fresh install and this thing is unbearable. 

I love my T41 and hate to move back to windows...
Even as I type this...my text is laging,

---

### Post by deadBee on 2010-02-07
I am new to ubuntu and having problems with opening/resizing/unminimizing windows and alt-tabbing. I can minimize the windows very fast but for the others, the screen freezes ( and the music player stoppes) for a second or two, which is really annoying.

I tried changing my codes into what you hav written but it didnt work.

Btw, the problems disappear if I deactivate extra windows effects)

---

