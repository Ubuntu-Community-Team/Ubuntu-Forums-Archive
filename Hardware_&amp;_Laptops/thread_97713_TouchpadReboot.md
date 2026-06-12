---
title: "Touchpad/Reboot"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by Doomed_Tupperware on 2005-12-01
How do I control my touchpad to click when I tap it, scroll down when I drag on the right side of it, etc? Oh, and I have a more annoying problem as well, when I   try to reboot my computer, it doesn't power down all the way and I have to manually turn it on and off.

---

### Post by mwhancock on 2005-12-02
I'm running the latest Ubuntu (with KDE desktop environment too) on a Sony Vaio laptop and am having the same exact problems.

I can't reboot the computer... and I have no idea how to control the touchpad. In my case, the touchpad is way to sensitive and I've got the cursor flying all over the place when I type... or I randomly, and accidentally, select stuff on webpages.

Someone, please help!

---

### Post by hw-tph on 2005-12-02
Depending on what kind of touchpad you have you will have different options. Today the most common touchpads with advanced features (tap-drag, back/forward scrolling, and so on) are either Synaptics or ALPS. There are articles on both in the wiki, and both use the excellent [Synaptics driver](http://web.telia.com/~u89404340/touchpad/). There are a lot of different configuration options to pass to the driver in /etc/X11/xorg.conf, so read up on the files in /usr/share/xorg-driver-synaptics/ (especially README.alps if you have an ALPS touchpad).

This works well for me using my ALPS touchpad:```
Section "InputDevice"
	Identifier	"ALPS"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"LeftEdge"			"120"
	Option		"RightEdge"			"830"
	Option		"TopEdge"			"120"
	Option		"BottomEdge"		"650"
	Option		"FingerLow"			"14"
	Option		"FingerHigh"		"15"
	Option		"MaxTapTime"		"180"
	Option		"MaxTapMove"		"110"
	Option		"EmulateMidButtonTime"	"75"
	Option		"VertScrollDelta"	"20"
	Option		"HorizScrollDelta"	"20"
	Option		"MinSpeed"			"0.3"
	Option		"MaxSpeed"			"0.75"
	Option		"AccelFactor"		"0.015"
	Option		"EdgeMotionMinSpeed"	"200"
	Option		"EdgeMotionMaxSpeed"	"200"
	Option		"UpDownScrolling"	"1"
	Option		"CircularScrolling"	"0"
EndSection
```

Note that you might have to replace /usr/X11R6/lib/modules/input/synaptics_drv.o with the latest version off of the website in order to have an ALPS working fully. The synaptics_drv.o in Breezy isn't really working well.

H&#229;kan

---

### Post by xyz on 2005-12-03
I don't have any problems with Touchpad on my Toshiba Satellite A40;however,I can't reboot either!Up until an hour ago,I could turn it off manually but now I have to pull out the plug and take out my battery??
Thanks and have a good weekend.

---

### Post by depp on 2005-12-03
check this thread, it's helpful.
[http://ubuntuforums.org/showthread.php?t=75314]("http://ubuntuforums.org/showthread.php?t=75314")

---

### Post by xyz on 2005-12-04
[QUOTE=depp]check this thread, it's helpful.
[http://ubuntuforums.org/showthread.php?t=75314]("http://ubuntuforums.org/showthread.php?t=75314")[/QUOTE]
Yes-thank you-that's where I found the solution.This is what worked for me:
```
Add reboot=h to the end of the kernel line in
```

sudo gedit /boot/grub/menu.lst

and the result is:
```
title           Ubuntu, kernel 2.6.12-10-686
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.12-10-686 root=/dev/hda3 ro quiet splash reboot=h
initrd          /boot/initrd.img-2.6.12-10-686
savedefault
boot
```

varanus's post:
"Guys, I found out the problem!

I posted to a bug report, and Matthew Garett was kind enough to give a fix. This issue will be fixed in dapper..."

Following up on depp's link,I found out that some people have other solutions to the same problem.

---

### Post by er-ku on 2005-12-04
Concerning the touchpad: You may want to give [GSynaptics](http://gsynaptics.sourceforge.jp/) a try. It lets you manually adjust settings for your touchpad in a GUI, but requires you to enable options in xorg.conf, that some people consider locally insecure. The choice is yours.

---

### Post by timmy334 on 2005-12-05
I know this gets old, but seriously... if you google "linux synaptics" if you have a synaptics touchpad, download the source and unpack it and read the README. The README is VERY well written and thoroughly explains EVERY available option for your touchpad.
Hint 1. if your trackpad has a scrolling area on the right, the ReghtEdge option sets that area. The smaller the number the farther to the LEFT you can use to scroll
Hint 2. The verticalscrolldelta sets speed in scrolling with it. If I remember correctly, the smaller the number the faster it scrolls. 
Hint 3. If you read the README you can easily set any option that those(qsynaptics, gsynaptics) programs set for your trackpad. It really is that easy. HTH

---

### Post by hw-tph on 2005-12-06
[QUOTE=timmy334]I know this gets old, but seriously... if you google "linux synaptics" if you have a synaptics touchpad, download the source and unpack it and read the README. The README is VERY well written and thoroughly explains EVERY available option for your touchpad.[/QUOTE]

Or just read the documentation that is already installed on your computer instead: /usr/share/doc/xorg-driver-synaptics/ is the location.



Håkan

---

