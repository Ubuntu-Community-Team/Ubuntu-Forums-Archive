---
title: "Adjusting touchscreen sensitivity on a Gateway tablet"
date: 2009-09-05
forum: Hardware
---

### Post by sinfony on 2009-09-05
Greetings,

I've managed to get the stylus working on a Gateway tablet that's been passed along to me, but it only registers strokes if I push extremely hard.  I haven't been able to find any way to adjust the sensitivity of the touchscreen.  Can it be done?  I'm running 9.04; I don't have the model number of the tablet (it doesn't appear to be printed anywhere on the unit), but it's a few years old, Core Duo processor, 1280x768 screen.  The stylus is a Finepoint MPP800.  I'd really appreciate any guidance on this!

---

### Post by Favux on 2009-09-05
Hi sinfony,

Is it possible the battery in the stylus is getting low?

Maybe you could post your xorg.conf?

---

### Post by sinfony on 2009-09-05
I have no idea about the stylus battery - as I mentioned, this tablet was passed on to me by somebody who no longer needed it.  Any ideas how to check it?

Xorg.conf:
```
Section "InputDevice"
         Identifier "Tablet"
         Driver "fpit"
         Option "Device"   "/dev/ttyS0"
         Option "MaximumXPosition" "12550"
         Option "MaximumYPosition" "7650"
         Option "MinimumXPosition" "400"
         Option "MinimumYPosition" "400"
         Option "InvertY"
         Option "Passive" "false"
         Option "TrackRandR"
         Option "SendCoreEvents"        "true"  
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier "Default Layout"
	Screen "Default Screen"
	InputDevice "Tablet"
EndSection
```

---

### Post by Favux on 2009-09-05
Hi sinfony,

Well nothing leaps out from your xorg.conf.

TrevT93 talks about the stylus battery on at least posts #31 & 34 on this thread:  [http://ubuntuforums.org/showthread.php?t=1221288&page=4](http://ubuntuforums.org/showthread.php?t=1221288&page=4)  Maybe you could PM him for advice.  That's probably what's wrong.  There must be some sites that show how to change the battery out.  Even if it's not "user serviceable" I'd hope you could google something up.

After a lot of thrashing around TrevT93 finally gets set up using:  [https://help.ubuntu.com/community/FujitsuStylus](https://help.ubuntu.com/community/FujitsuStylus)  My guess is it was adding the serial line to /etc/rc.local.

I hope this is helpful.

---

