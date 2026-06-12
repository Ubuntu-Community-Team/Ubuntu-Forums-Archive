---
title: "wacom bamboo pressure sensitivity in ubuntu 7.10"
date: 2008-08-16
forum: Hardware
---

### Post by miabe on 2008-08-16
hi,

I have xubuntu 7.10 running on my eeepc and with the help of this forum and this thread 

[http://ubuntuforums.org/showthread.php?t=631881](http://ubuntuforums.org/showthread.php?t=631881)

I got my bamboo to work quite quick! thanks a lot as I am a linux newbie.

The only thing I can't get to work is the pressure sensitivity. Absolute mode works, keys work, wacomcpl works.
I am not sure if I am missing some options in gimp or entry in xorg.conf to get it to work.

Any help appreciated :D
cheerio, mia

---

### Post by miabe on 2008-08-28
no one using the bamboo with pressure sensitivity?
any recommendation for an alternative?

---

### Post by miabe on 2008-09-04
what a pitty :/

---

### Post by whizbaby on 2008-09-09
Heh u impatient :p
But seriously, i got a bamboo one working WITH pressure sensitivity (since today) and didnt forget about you :)
Take a look at this link, you should be able to tweak your xorg.conf to work properly after reading(not the whole of course):
[http://ubuntuforums.org/archive/index.php/t-25151.html](http://ubuntuforums.org/archive/index.php/t-25151.html)
Works fine for me in gimp and inkscape.
GreetZ
p.s.:forgot to mention: im on 7.10,too

---

### Post by miabe on 2008-09-10
hi whizbaby!

thanks a lot for the link! I had everything set up already but didn't activate it in the gimp preferences... now it works :)
but in the gimp the pressure is only working in 4 steps. I tried to play with the pressure curve parameter but without sucess.
any idea what else I could try?

---

### Post by whizbaby on 2008-09-15
HiZ,
could you please post the wacom-related
lines of your xorg.conf?

---

### Post by miabe on 2008-09-15
sure!

```
Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
	Option		"PressCurve"	"50,0,100,50"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
#	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
	Option		"USB"		"on"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"pad"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"pad"
	Option		"USB"		"on"
EndSection
```

---

### Post by whizbaby on 2008-09-15
I guess you just have to play around with the PressCurve parameters.
I have
x1 y1 x2 y2

0,5,95,100
and can work well with it. Ill explain how it works so you can play around to find a setting that meets your needs.

If I got it right, the 'presscurve' is always a bezier curve defined by lines (0,0,x1,y1) and (x2,y2,100,100). If you dont know what the hell that is (like probably most non-mathematicians) you can get an impression of how it looks like by downloading and installing tablet-apps:
[http://www.alexmac.cc/tablet-apps/](http://www.alexmac.cc/tablet-apps/)

once downloaded, you can install with
```
sudo dpkg -i tablet-apps_0.3.1-0_i386.deb
```

launch it (tablet-capplet.py from the commandline) and choose 'stylus'.
Now you will see a pressure curve simulator, with two yellow draggable points. Take your bamboos pen and start to drag them a bit around. See how the curve behaves? What you do in xorg.conf is setting the values of the coordinates of the first point x1,y1 and of the second point x2,y2. So now you can understand why the presscurve provided by the site I mentioned leaves you with the impression of only having 4 stages...sorry for that!

Although it might sound complicated, the installation is really easy and the program intuitive + theres a test drawing area, so you should be able to tweak your settings with that.

---

### Post by miabe on 2008-09-15
perfect!
that tool helped me a lot in finding the right values!
thanks again :)

---

### Post by whizbaby on 2008-09-15
Np its nice to share when I put much time in it to make it work for myself ;)

---

