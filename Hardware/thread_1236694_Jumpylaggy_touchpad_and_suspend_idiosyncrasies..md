---
title: "Jumpy/laggy touchpad and suspend idiosyncrasies."
date: 2009-08-10
forum: Hardware
---

### Post by tonyisntcreative on 2009-08-10
(This was originally posted on the [Arch Linux forums]("http://bbs.archlinux.org/viewtopic.php?id=77693"), but since I'm looking for some help ASAP I've decided to get it on a few other message boards as well.  Excuse what might seem Arch-biased langauge.)

I just got a hold of an older laptop, a Dell Latitude C640, and to my dismay setting up Linux on it hasn't been the walk in the park I'd hoped it'd be.  I read a bunch of articles about Linux on this machine before I got it and most seemed to have a pretty easy time of everything.  Of course this might be because the laptop is quite a few years old and older Linux kernels acted different ways, but I guess I assumed that things would be even easier using a modern distro.

**The Touchpad**
It worked fine on the install of Windows XP that came installed on it, with no problems at all.  Before installing any flavor of Linux I ran Knoppix on it just kind of to make sure things would go OK.  It was a little dated, being Knoppix 5.10, but I figured it'd do for my purposes.

The first time I booted it seemed to work OK, with the mouse cursor behaving mostly as it should, with a little lag.  I've used this same Knoppix disk on another laptop and it did much the same thing.  After another boot, however, I saw that things weren't going to be so easy.  The cursor immediately drifted off into one of the screen's corners (it didn't seem to care much which one it was in, as long as it was in one) and would refuse to come out.  I could move the cursor a little ways off of the edge of the screen, but not far enough to click anything, and it would immediately go back as soon as I released my finger.  So I tried a few other disks.  First I tried a CD I have for Crunchbang Linux (just a minimalist, Openbox-based Ubuntu flavor), and then Knoppix 4.  Both gave very similar results.  Crunchbang let me have a little bit more control over the cursor for a little while after booting, maybe for about a minute, and then the same behavior cropped up.  I only booted with Knoppix 4 once, but it was pretty much the same deal.

I started reading up on what might be going on and came across [a thread on the Linux Mint forums](http://forums.linuxmint.com/viewtopic.php?f=90&t=27670&) that seemed to be describing an issue very close to mine (though mine is completely unrelated to the AC adapter and persists whether it's plugged in or not).  Someone in the thread suggested it was a kernel issue, since it's definitely not a hardware issue, so I then booted into a copy of DSL I had lying around, which uses the 2.4 kernel.  Sure enough everything worked without problems.  This caused me to believe, going by some of the conclusions from the Lnux Mint thread and apparently mistakenly, that the issue may have been with the 2.6 Debian kernels, so I figured I'd just get Arch installed and see how things went.

After getting X set up and working properly I saw that the issue was going to be much the same.  To get around the cursor being dragged into the corner against my will I found out that if I ran without HAL or that if I disabled hot-plugging I could use the touchpad, although not flawlessly.  Here's xorg.conf:

```
Section "ServerLayout"
	Identifier	"Xorg"
	Screen		0 "Default" 0 0
	InputDevice	"Touchpad"	"CorePointer"
#	InputDevice	"USB Mouse"	"SendCoreEvents"
EndSection

Section "ServerFlags"
	Option		"AllowMouseOpenFail"	"true"
	Option		"AutoAddDevices"	"false"
EndSection

Section "Module"
	Load		"glx"
	Load		"dri"
	Load		"drm"
	Load 		"synaptics"
EndSection

Section "InputDevice"
	Identifier	"Touchpad"
	Driver		"synaptics"
	Option		"SHMConfig"	"true"
	Option		"AlwaysCore"	"true"
	Option		"MinSpeed"	"0.05"
	Option		"MaxSpeed"	"0.40"
	Option		"TapButton1"	"1"
	Option		"TapButton2"	"2"
	Option		"FastTaps"	"1"
	Option		"VertEdgeScroll"	"true"
	Option		"HorizEdgeScroll"	"true"
	Option		"Emulate3Buttons"	"true"
EndSection

#Section "InputDevice"
#	Identifier	"USB Mouse"
#	Driver		"evdev"
#	Option		"SendCoreEvents"	"true"
#EndSection

Section "Monitor"
	Identifier	"LCD"
EndSection

Section "Device"
	Identifier	"Radeon Mobility 7500"
	Driver		"radeon"
EndSection

Section "Screen"
	Identifier	"Default"
	Device		"Radeon Mobility 7500"
	Monitor		"LCD"
	DefaultColorDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Group		"video"
	Mode		0666
EndSection
```
The "AutoAddDevice" option is the only thing that seems to make any difference in usability at all; without it I can't use the touchpad at all, and with it I can, but to varying degrees.  I've found that right after I boot up everything seems to work exactly how it's supposed to, but shortly after, sometimes 15 seconds, sometimes many minutes, things seem to get kind of unresponsive.  The cursor will go where I want it to go, but it jumps around and does it very slowly.  The mouse buttons also get very unresponsive.  Right click is especially bad, and I often have to hold down the button just to get it to do what I want, but left click is very bad too, requiring me to push the button down for almost a full second, sometimes several times.  Taps on the pad, after things go wrong, also stop being recognized, forcing me to use the buttons (which I'm OK with).  It's usable, but the behavior is not ideal whatsoever—it's rather annoying.

The most aggravating thing, I think, is that I can't seem to find anyone else using this same model that has this issue.  The latest I've seen is from January: [An Ubuntu (8.10) user reports no issues and is very pleased](http://www.linlap.com/wiki/dell+latitude+c640) (see comments at the bottom of the page).

**Suspend (both to disk and RAM)**
I actually did install the latest Crunchbang (9.04.01, the 32-bit "Lite" edition) first to see if anything would clear up by installing it rather than running the live CD, but I only had it installed for a few hours.  I didn't really get into messing with xorg.conf that much yet, only really touching "FingerLow" and "FingerHigh" settings, so the touchpad issue was still nagging me.  I did play around a bit though and found out that suspend to RAM and suspend to disk worked pretty much from the go, only requiring that I installed uswsusp.  Issuing a simple "sudo pm-suspend" or "sudo pm-hiberate" put the computer to sleep and it woke back up without any issue at all.

But suspend on Arch is proving to be a pain in the neck.  Suspend to RAM simply will *not* work; the computer shuts down but will not resume, leaving me only a blank screen with an unresponsive keyboard.  Suspend to disk works (using hibernate-script as pm-hibernate doesn't seem to do anything at all), but it works very poorly; both suspending and resuming take a very, very long time—so long, in fact, that I'm just better off shutting down and restarting normally, since the boot time is better.  I don't know what accounts for the drastic difference in distros, and this isn't the first experience I've had with suspension working on Ubuntu but not on Arch.  What is different in the Ubuntu implementation of pm-utils than the Arch way?  Is it the Ubuntu kernel?  Is there any way to implement the Ubuntu way with Arch (because, after all, I'd prefer to use Arch)?

I'm considering installing Crunchbang once again if I can't get things to work the way I want them to in the next few days on Arch.  And, if I can't make the touchpad work in a satisfactory manner on Cruchbang, I might just have to reinstall Windows.  I don't want to do that. :/

---

### Post by tonyisntcreative on 2009-08-11
Bump.

---

### Post by tonyisntcreative on 2009-08-13
Final bump.  I think I might have to stick with Windows for a while. :/

---

