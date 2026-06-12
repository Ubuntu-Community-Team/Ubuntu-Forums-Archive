---
title: "Dell XPS m1530 touchpad"
date: 2008-04-22
forum: Hardware
---

### Post by ZeRoNiXxX on 2008-04-22
OK, first of all I'm new so bear with me, I have Ubuntu 7.10 installed alongside Vista, everything was working fine until I updated Ubuntu for the first time and now the mouse just flies around the screen like it's a little too happy to see me every time I use the touchpad, and it's an Alps trackpad.
it works fine when I am using a Microsoft mouse, ironic, isn't it.

help would be appreciated

---

### Post by jespdj on 2008-04-23
You probably have BIOS version A08 on your XPS M1530. Solution: Use the following kernel parameter when booting Ubuntu:
```
i8042.nomux=1
```
From [here](http://ubuntuforums.org/showthread.php?t=737060).

Also see my page: [http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530](http://jesperdj.pbwiki.com/Ubuntu-on-the-Dell-XPS-M1530)

---

### Post by karl0sglover on 2008-04-26
Hello,

A few days ago i got my XPS M1530, on 8.04 the mouse has a mind of its own when you move it i have tried the above in the kernel options still does the same thing. It's not a sensitivity issue i have played around with this for numerous hours.

(Works fine on previous versions of Ubuntu)

If you move the mouse it does not move, play with it a bit and it does but very fast although it tends to go to menus or create folders if you do move it.

I am running the latest BIOS as i saw a similar issue was fixed by downgrading to A7.

Any further suggestions would be greatful.

Thanks.

---

### Post by ZeRoNiXxX on 2008-05-09
Thanks, that was the problem.

---

### Post by phamnewan on 2008-05-21
> **karl0sglover said:**
> Hello,

A few days ago i got my XPS M1530, on 8.04 the mouse has a mind of its own when you move it i have tried the above in the kernel options still does the same thing. It's not a sensitivity issue i have played around with this for numerous hours.

(Works fine on previous versions of Ubuntu)

If you move the mouse it does not move, play with it a bit and it does but very fast although it tends to go to menus or create folders if you do move it.

I am running the latest BIOS as i saw a similar issue was fixed by downgrading to A7.

Any further suggestions would be greatful.

Thanks.

The example had a typo for the letter "l" instead of "i"

I put it in exactly the same with the "i" and it worked fine.

---

### Post by toozler on 2008-07-27
Sorry for bringing this topic back.

That solution works for me, but still, the touchpad is extremely not sensible. To bring the cursor from the left end of the screen to the right, I did swipe my finger 5 times (1650x1050 screen res).

Any tips on how to increase sensitivity?

---

### Post by Brain Bug on 2008-08-01
Hi, 

I also have an XPS M1530, and the touchpad was crazy and not sensible.
I found some help in different forums to increase sensitivity.
Here is the corresponding section in my xorg.conf

```
Section "InputDevice"
       	Identifier    	"Synaptics TouchPad"
       	Driver        	"synaptics"
       	Option        	"SendCoreEvents"    "true"
       	Option        	"Device"    "/dev/psaux"
       	Option        	"Protocol"    "auto-dev"
       	Option        	"SHMConfig"    "true"
       	Option        	"HorizEdgeScroll"    "1"
     	Option      	"MinSpeed"      "0.75"
       	Option      	"MaxSpeed"      "0.75"
       	Option      	"AccelFactor"      "0.020"
       	Option      	"EdgeMotionMinSpeed"   "200"
       	Option      	"EdgeMotionMaxSpeed"   "200"
EndSection
```

I have a 1680*1050 px screen, and the width of the touchpad is enough for me to cover all the screen's width.

Unfortunately, I still do not have the vertical and horizontal scroll working fine....


Hoping it will be helpful.

---

