---
title: "Ibm ThinkPad T42 (ubuntu 10.04) buttons, graphic, fingerprint"
date: 2010-07-26
forum: Hardware
---

### Post by vestit on 2010-07-26
Hello, I install ubuntu 10.04 on my  IBM ThinkPad T42. Very nice and friendly OS, but I have some problems: Fingerprint doesn't work
IBM buttons doesn't work (when you press volume up/down, mute, Access IBM nothing happens) WiFi, Light, Brightness buttons work but in screen doesn't show OSD (for example brightness level)
TrackPoint Scroll problem I already solved
Video card driver needed

Leptop config: Intel Pentium 1.7
                       HDD 40 GB
                       RAM 1 GB
                       Video card ATI Radeon 7500

Help me to solve this problems.
Waiting for yours replay with instruction.
Thanks.

---

### Post by vestit on 2010-07-26
Here instructions how to solve problem with TrackPiont Scrolling

**Step 1. Create a new file**

sudo nano /usr/lib/X11/xorg.conf.d/20-thinkpad.conf

 **Step 2. Insert the following**

Section "InputClass"
	Identifier	"Trackpoint Wheel Emulation"
	MatchProduct	"TPPS/2 IBM TrackPoint|DualPoint Stick|Synaptics Inc. Composite TouchPad / TrackPoint"
	MatchDevicePath	"/dev/input/event*"
	Option		"EmulateWheel"		"true"
	Option		"EmulateWheelButton"	"2"
	Option		"Emulate3Buttons"	"false"
	Option		"XAxisMapping"		"6 7"
	Option		"YAxisMapping"		"4 5"
EndSection

 **Step 3. Save file, restart computer, and enjoy!**

---

### Post by rCXer on 2010-07-26
For the OSD problems take a look at [this well known bug](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/357673?comments=all).  If you read through the comments (and there are alot of them) you may find a workaround.  

[Here]("http://www.thinkwiki.org/wiki/How_to_enable_the_fingerprint_reader_with_ThinkFinger") are general instructions for using the fingerprint reader. [Here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.10_%28Karmic_Koala%29_on_a_ThinkPad_T61#Enabling_the_fingerprint_reader")'s another article for T-series machine with Karmic.  It may work for lucid.

---

### Post by vestit on 2010-07-27
Thank you for your replay. I will try to solve the problems by your instructions, and what's about Video card driver ? ( Ati Radeon 7500 )

---

### Post by rCXer on 2010-07-27
If you run Linux on a ThinkPad, [ThinkWiki]("http://www.thinkwiki.org") is your friend.  I have a t43p and the site helped me alot.

The proprietary driver, [fglrx]("http://www.thinkwiki.org/wiki/Fglrx"), has some extra features.  Unfortunately fglrx [does not support]("http://www.thinkwiki.org/wiki/Fglrx#ThinkPads_that_are_NOT_supported_by_fglrx") your machine.

---

### Post by imagecko on 2010-08-31
Please write here if you got everything working on a T42.

---

### Post by vestit on 2011-04-11
Everything was working, but OSD i can't fix it...
But now it's not actual because I change my pc, but may be this information be helpful  to someone.
Thank you for your help.

---

### Post by Kanehekili on 2011-07-14
I'm running a T42 with Lucid. The fix for the OSD was easy and straightforward:

sudo gedit /etc/rc.local

insert line before exit:
sudo cp /sys/devices/platform/thinkpad_acpi/hotkey_all_mask /sys/devices/platform/thinkpad_acpi/hotkey_mask

That might lead to an erromessage in dmesg, but it works.

---

