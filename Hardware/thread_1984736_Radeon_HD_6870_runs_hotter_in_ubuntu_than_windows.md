---
title: "Radeon HD 6870 runs hotter in ubuntu than windows"
date: 2012-05-22
forum: Hardware
---

### Post by hg088 on 2012-05-22
I installed the .run driver from the amd page.

With 50% fan speed the temp i get is abput 54C.

The thing is that when i'm in windows with 50% fan speed the temp is 41C tops.

I think this problem has something to do with the clocks been always at max in ubuntu (even when idle):


Default Adapter - AMD Radeon HD 6800 Series 
                            Core (MHz)    Memory (MHz)
           Current Clocks :    900           1050
             Current Peak :    900           1050
  Configurable Peak Range : [775-1000]     [1050-1250]
                 GPU load :    0%


and in windows the current clocks are at 300 when idle.

I wish someone helps me understand why in ubuntu the clock are always so high

---

### Post by Redblade20XX on 2012-05-22
The software provided for windows is more refined than the linux ports. AMD spends a lot more time on the window driver than the linux. That's one possible solution. You can try the open source drivers in which you have a little bit more control over and can up to a certain extent, modify them. That is if the heat problem is really bothering you!

-Red

---

### Post by lukeiamyourfather on 2012-05-22
A lack of power management in the drivers might have been the case years ago but things have improved quite a lot just in the last year or two. The FGLRX driver from AMD has various power management features. It might be running at the higher clock in Linux if the desktop interface being used requires 3D acceleration (Unity, GNOME 3, etc.). You could try an alternate desktop interface and see if that makes a difference (GNOME Classic, Unity 2D, Xfce, etc.).

---

### Post by hg088 on 2012-05-22
Hmm same clock speeds on unity 2D :/  I installed the propietary driver cause i was trying to install starcraft 2 in ubuntu (the only game i play and) but sadly i havent been succesful. Now im thinking to go back to the opensource driver, how can i control fan speed of the card  without the propietary driver?

---

### Post by Redblade20XX on 2012-05-23
> **hg088 said:**
> Hmm same clock speeds on unity 2D :/  I installed the propietary driver cause i was trying to install starcraft 2 in ubuntu (the only game i play and) but sadly i havent been succesful. Now im thinking to go back to the opensource driver, how can i control fan speed of the card  without the propietary driver?

First check your BIOs and see if there are any options to control the fan speed such as FAN always on, etc. Most systems have there hardware controls in the BIOs to avoid software screw ups! You should also be able to play around with thermal levels if there is an advance BIOs section.

-Red

---

### Post by hg088 on 2012-05-23
I found an acceptable solution to this problem ([http://superuser.com/questions/270431/over-underclock-5870-on-linux-without-limits]("http://superuser.com/questions/270431/over-underclock-5870-on-linux-without-limits"))

AMDOverdriveCtrl allowed me to set static clock speeds for my GPU so i set the clock to the speeds i read in windows and now the temps are equal. Now i have to run this on boot and dont have dymamic clocks but at least my temps are low

---

### Post by hg088 on 2012-05-24
Jmm, i found out that when i disabled my second monitor (using the catalyst driver) the frequencies and temperatures behave just like in windows :D

Silly me as always, not noticing this sooner

---

