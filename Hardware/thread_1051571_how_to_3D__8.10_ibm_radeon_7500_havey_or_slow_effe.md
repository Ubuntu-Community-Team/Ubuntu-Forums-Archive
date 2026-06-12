---
title: "how to 3D  8.10 ibm radeon 7500 havey or slow effects"
date: 2009-01-26
forum: Hardware
---

### Post by sam1948 on 2009-01-26
after lot's of frustration (~:

before u start, run this. if it fails u will be able to restore original xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkupBefor
```

run in terminal
```
sudo aptitude install xserver-xorg-video-radeon xserver-xorg-video-ati
```

type in terminal
```
sudo gedit /etc/X11/xorg.conf
``` 
in the section
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
change it by adding the following lines
```
Section "Device"
	Identifier	"Configured Video Device"
	[B]Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "AGPMode" "4" 
	Option "AGPSize" "64"
	Option "RingSize" "8"
	Option "BufferSize" "2"
	Option "EnablePageFlip" "true"
	Option "EnableDepthMoves" "true"
	Option "RenderAccel" "true"
	# Eyecandy Stuff
	Option "AccelMethod" "4"
	Option "EnablePageFlip" "true
	Option "DDCMode"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"[/B]
EndSection
```

now restart x-server (alt+ctrl+backspace) or restart computer
that's all graphics are as fast as no vista could ever dream on with 16Mb video card
enjoy...

---

### Post by Sunflower1970 on 2009-02-01
Awesome. Thank you for this. My 3D effects are speedy again :)

---

### Post by bomanizer on 2009-02-10
Thank you! This is awesome.

---

### Post by gijoe3k on 2009-02-12
Sam1948, you are great!! Thanks to you i am now able to use my Thinkpad t30 to it's graphical potential! :guitar: 

I felt that I was going to have to recreate the wheel again to get my radeon 7500 working. You rock man! ^_^

---

### Post by sam1948 on 2009-02-13
I glad I could help (:

---

### Post by zhork on 2009-04-28
thanks!

---

### Post by emeraldgirl08 on 2009-04-28
Is there anyone who could walk me through this on PM???

I've noticed my overall effects aren't as smooth as they should be (ie. laggy scrolling, etc). 

Thank you.

:KS

---

### Post by emeraldgirl08 on 2009-04-29
:P

Hey it worked!

Wasn't too hard to do :)

Thanks!

---

### Post by MrWES on 2009-05-01
> **sam1948 said:**
> after lot's of frustration (~:

before u start, run this. if it fails u will be able to restore original xorg.conf
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkupBefor
```

run in terminal
```
sudo aptitude install xserver-xorg-video-radeon xserver-xorg-video-ati
```

type in terminal
```
sudo gedit /etc/X11/xorg.conf
``` 
in the section
```
Section "Device"
	Identifier	"Configured Video Device"
EndSection
```
change it by adding the following lines
```
Section "Device"
	Identifier	"Configured Video Device"
	[B]Driver		"radeon"
	BusID		"PCI:1:0:0"
	Option "AGPMode" "4" 
	Option "AGPSize" "64"
	Option "RingSize" "8"
	Option "BufferSize" "2"
	Option "EnablePageFlip" "true"
	Option "EnableDepthMoves" "true"
	Option "RenderAccel" "true"
	# Eyecandy Stuff
	Option "AccelMethod" "4"
	Option "EnablePageFlip" "true
	Option "DDCMode"
	Option "SubPixelOrder" "NONE"
	Option "ColorTiling" "false"[/B]
EndSection
```

now restart x-server (alt+ctrl+backspace) or restart computer
that's all graphics are as fast as no vista could ever dream on with 16Mb video card
enjoy...

I happened to get my hands on an old T41 with an ATI 7500 video card, and your post was spot on! I can't believe the performance I get with compiz enabled on this 16MB card. Thank you very much for the information on modifying my xorg.conf -- golden!

Bill

---

### Post by sailor420 on 2009-05-04
Thanks for this... My performance isn't perfect, but it is quite a bit better than it used to be now!

---

### Post by paulo.thecure on 2009-09-09
Is this only for IBM or does it work also in Asus L3800C with the same hardware ?

Thanks

---

### Post by sam1948 on 2009-09-16
> **paulo.thecure said:**
> Is this only for IBM or does it work also in Asus L3800C with the same hardware ?

Thanks

i guess it'll work. but there is no guarantee

---

### Post by fusuikan on 2010-08-24
Thanks so much.  I was about to abandon Ubuntu for this sole reason.  Much to my chagrin.  I am so stoked that I can watch HD Video again.  

Thanks!

---

### Post by mikey on 2010-09-19
a31 thinkpad with ati 7500 video card 
like others have not been able to load appropriate driver. have followed this thread but when I "gedit /etc/X11/xorg.conf," I get just a blank document without any device listings of any kind.
can someone illuminate my problem for me so I can follow sam's recipe.
thanks
mike

---

### Post by Pas_sa on 2010-09-29
I too have this problem, and since Ubuntu hasn't used an xorg.conf file since 9.10 or something, I'm not sure how to follow this guide any more..

How is the process different in the latest versions of Ubuntu?

---

