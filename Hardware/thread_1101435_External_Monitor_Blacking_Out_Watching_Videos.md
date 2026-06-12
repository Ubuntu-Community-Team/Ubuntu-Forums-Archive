---
title: "External Monitor Blacking Out Watching Videos"
date: 2009-03-20
forum: Hardware
---

### Post by theSuperman on 2009-03-20
I have been having this problem for a while.  I have an EEEpc model 1000 with the Easy Peasy distro of ubuntu (8.10).  I use xrandr to change my resolution to hook up my computer to an external monitor.  This works fine 100% of the time, until I go and watch a video.  This can either be a video watched through totem/mplayer/vlc or a flash video watched on Firefox.  Randomly, the screen will just black out.  I can use my key shortcuts to bring up a terminal and blindly type and change my  resolution to be back onto my laptop's internal screen.  This screen still works.  I am then unable to use my external monitor until I do a system restart.  Restarting X does not do anything.  

Is there some kind of log file I can look at to help determine what is happening when this blackout occurs?

---

### Post by tankfists on 2009-06-04
Interesting. I'm having a similar problem. I have an Asus eeepc 1000HE. I do not experience any problems with this external monitor in windows. However, under the Jaunty the screen blacks out randomly. I was not watching a video at the time, however.

There aren't any errors in the Xorg log and the only warnings are these: 

(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
(WW) intel(0): libpciaccess reported 0 rom size, guessing 64kB
(WW) intel(0): Register 0x61200 (PP_STATUS) changed from 0xc0000008 to 0xd000000a
(WW) intel(0): PP_STATUS before: on, ready, sequencing idle
(WW) intel(0): PP_STATUS after: on, ready, sequencing on
(WW) intel(0): Register 0x61114 (PORT_HOTPLUG_STAT) changed from 0x00000b00 to 0x00000800
(WW) intel(0): DRI2 requires UXA
(WW) Asus EeePC extra buttons: unable to handle keycode 372


All of which are cryptic to me.
This is my Xorg file:

```

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
		Virtual	2048 2048
	EndSubSection
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection
```

Any ideas?

---

