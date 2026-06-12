---
title: "Toshiba Satellite Pro A120 laptop and external Samsung SyncMaster 913N monitor."
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by quixotic-cynic on 2007-08-14
Using an external Samsung SyncMaster 913N monitor on a Toshiba Satellite Pro A120 laptop (ATI display adapter) results in a 1280x800 resolution (laptop screen) showing aprox 70% of the screen (with default xorg.conf). This was why I gave up on Linux for the n-th time about 6 months ago (spent ages on it) but I thought I would give it another try - still haven't got it working though. I don't have much time left before I will have to format my HDD and reinstall windows again (for now).

I do not want/need a dual monitor setup - just my external monitor to look right when I am using it (i.e. use 1280x1024 resolution).

The xorg.conf is using the 'ati' driver. My display adapter appears to be an ATI Technologies, Inc. Radeon Xpress 200M (RC410).

Tried:
* Running <"sudo dpkg-reconfigure -phigh xserver-xorg"> in the terminal.
* Adding "1280x1024" in the Modes sections.
* Option "TwinViewOrientation" "Clone" and Option "MetaModes" "1280x800,1280x1024" in device section.
* Option "MonitorLayout" "CRT,LFP" & Option "Clone" "true" in monitor section.
* Using Modeline "1280x1024@75i" 64.12 1280 1312 1552 1584 1024 1046 1054 1077 interlace
* Imitating [http://ubuntuforums.org/showthread.php?t=522316](http://ubuntuforums.org/showthread.php?t=522316)
* Imitating [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/)
* Reading threads here, on Linux Questions and the Fedora forums.

Below is an example of one of my attempts, including them all would take too much space (part of xorg.conf file):

[Edit: Removed example, see below]

I am begining to go (more) insane and am having nightmares of gaint hell-spawned Xs chasing me... any help you are able (and willing) to provide would be much appreciated.

Thank you.
-- a quixotic cynic

---

### Post by heidfirst on 2007-08-14
I have pretty much the same problem with a fujitsu siemens amilo pro V3505 and a sun microsystem 19in monitor.  I currently have two separate xorg.conf files one for the external monitor and one for the laptop display.  

At present I have not worked out howto merge the two files.  I know this does not answer your question but you are not the only one struggling with xorg.

---

### Post by quixotic-cynic on 2007-08-14
"I currently have two separate xorg.conf files one for the external monitor and one for the laptop display."

I haven't even got it working like that yet...

"At present I have not worked out how to merge the two files."

Try the [http://ubuntuforums.org/showthread.php?t=522316](http://ubuntuforums.org/showthread.php?t=522316) and [http://ozlabs.org/~jk/docs/mergefb/](http://ozlabs.org/~jk/docs/mergefb/) pages if you haven't all ready - the latter one is probably the best. I think that is the way you would do it (theoretically)...

"I know this does not answer your question but you are not the only one struggling with xorg."

Heh, believe me, I know - there are a great many of these threads and very few answers. I suspect most people just give up in the end. Thanks for the reply at least...

Edit:

On a test of live CDs:

* 1280x1024 as desired: FreeSBIE (FreeBSD)
* 1024x768 - DSL and, after Fn+F5ing, SimplyMEPIS
* Failed (i.e. lame screwed up res): Knoppix, Xubuntu, gNewSense and Fedora 7 (even after playing with xorg and stuff).

*bashes head against wall*

I think I may have to work out how to install FreeBSD... (I know it does not have a "nice friendly installer")...

[Edit 2]
Here is a working instance for this setup - as with heidfirst's conf files, it will only get the external monitor working.
I had to use the 'vesa' driver - which is probably not good, but at least it damn well works.

<Use these:>

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon Xpress 200M (RC410)"
	Driver		"vesa"
	BusID		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	# 1280x1024 @ 75Hz (VESA) hsync: 80.0kHz
	ModeLine "1280x1024" 135.0 1280 1296 1440 1688   1024 1025 1028 1066 +hsync +vsync
EndSection

<And each modes line should be:>
Modes		"1280x1024" "1280x800"


That is gonna be it from me for now - it works well enough and I have work to do...
--QC

UPDATE: Upgrading to Ubuntu 7.04 has resulted in better support - by default the display is usable in 1024x768. When the Modes line is modified in xorg.conf the display works fine.

---

