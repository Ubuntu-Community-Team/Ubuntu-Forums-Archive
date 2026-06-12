---
title: "Driver Issues With ATI Radeon HD 5850"
date: 2010-01-24
forum: Hardware
---

### Post by curtissthompson on 2010-01-24
_**My problem:**_
I recently built a new PC and installed Ubuntu 9.10 Karmic Koala (as the only operating system) on the system.  I'm using a Sapphire ATI Radeon HD 5850 graphics card on this system and after the installation the display worked fine except when I changed any display settings, such as resolution (which was set to 1600x1200 on a 17inch CRT that has a native resolution of 1024x768), the screen and colors would become very distorted.  So I proceeded to install the driver for my graphics card by going to System > Administration > Hardware Drivers.  The only driver displayed was the ATI Proprietary FGLRX Driver, so I installed it and restarted my system (I'm not sure what version of the FGLRX driver it was, because it didn't list the version, but presumably the most recent 9.12 I'd imagine).

Upon restart my display resolution went from 1600x1200 before to something like 800x600 or 640x480  after.  Any time I attempted to change this resolution, the colors and display would become distorted like I mentioned above before the installation of the driver.  Additionally, there was an "AMD Unsupported Hardware" watermark displayed in the lower right hand corner of my screen.  If that wasn't enough, my screen would constantly turn on and off about 10-15 times rapidly, then stop for about a couple minutes and do it again in an endless cycle.  I've since uninstalled the ATI Proprietary FGLRX Driver and am able to get by without a fix temporarily.

_**My question is:**_
Are there any solutions to this driver issue?  Or are there any open source or alternative drivers I can use that work better?  I've searched and read seemingly endless accounts of similar issues on a whole variety of ATI cards ranging from quite old to very new, that provided no clear solution to the issue.  While my system in its current state is functional, it is barely so.  I need a solution to this problem, as I really can't afford to buy an Nvidia card because of ATI driver issues.

Any help is greatly appreciated!

*EDIT: [SOLVED] Solution to this problem is available at this [thread]("http://ubuntuforums.org/showthread.php?t=1394562") and involved downloading and installing ATI Catalyst Driver version 10.1.

---

### Post by Yellow Pasque on 2010-01-25
> (I'm not sure what version of the FGLRX driver it was, because it didn't list the version, but presumably the most recent 9.12 I'd imagine).

It was probably 9.10, which was what came with Ubuntu Karmic. Try installing the latest 9.12 from ATI's site (or wait a week or so for 10.1)

---

### Post by markbuntu on 2010-01-25
Hardware manager supp;ies the 9.10 driver which does not fully support the 5xxx cards. The latest 9.12 driver does. There is also a hotfix for the 9.12 that came out shortly after the driver was released. I am not sure if this got incorporated into the 9.12 driver available at the site. As temujin suggests you might want to wait a few days for the 10.1 driver.

Be sure to remove completely the driver you have now before installing a new one or you will have guaranteed problems with kernel updates.

---

### Post by abhiroopb on 2010-02-09
I am planning on buying the HD5850. Would you say the support is good for it?

I have actually just started a thread about it here: [http://ubuntuforums.org/showthread.php?p=8802107#post8802107](http://ubuntuforums.org/showthread.php?p=8802107#post8802107)

I should have the computer by the end of next week. Where would I get the driver from? How would I update it? Would dual monitors work?

---

### Post by mickie.kext on 2010-02-09
I would suggest that you steer away from ATI HD5xxx if you want to use Linux, unless you are X server developer. AMD's proprietary FGLRX drivers are broken mess, and are not worth using. Open source drivers are fine but HD5xxx are not yet fully supported and won't be for a while. DRI for it has landed in Linux 2.6.33 but Karmic use 2.6.31

---

### Post by Botruckle on 2010-03-20
I'm using the ATI Radeon HD 5850 with the 10.2 drivers on Ubuntu 9.10 (64bit). Movies look great. No fancy games installed yet, but the built-in games are fine. I ran one older 32bit game (Giants: Citizen Kabuto) under Wine and it works for the most part, but some effects are poorly rendered.

---

### Post by dispie on 2010-05-01
I moved this question to its own topic please see 
[http://ubuntuforums.org/showthread.php?t=1469003](http://ubuntuforums.org/showthread.php?t=1469003)



i have been trying to figure out what system to buy because of Ubuntu support 

Currently running 10.04 on my server and eeebuntu 3 nbr on my asus eee works great.

But my boss is paying for a new system that will be a multi boot between windows 7 ulti 64b (sorry for the dirty word) and ubuntu 10.04

I know Nvidia is the linux choice but kinda lost the game to Ati. And the new 480 cards I cant find if they are already supported. 

So i kinda don't know what to get, here are the specs of the 2 systems im looking at: 

Cooler Master ATCS 840
Corsair HX850W
Gigabyte GA-X58A-UD7
Intel Core i7 930
OCZ Reaper OCZ3RPR1600LV6GK
[COLOR="Red"]Intel performance ssd 80Gb (maybe problem don't know how ubuntu reacts to this)[/COLOR]

[COLOR="Red"]2x Sapphire HD5850 Vapor-X 1GB crossfire way faster and cheaper then a Nvidia 480 card (but does Ubuntu run this a single one I already read mixed things about some say it works great some say stay away) [/COLOR]

**2nd option **

Cooler Master ATCS 840
Corsair HX850W
Intel Core i7 860
Gigabyte GA-P55A-UD7
Corsair Dominator CMD8GX3M4A1600C8
Intel performance ssd 80Gb 
[COLOR="Red"]Gigabyte GeForce GTX480 (can't find anything on the support of the new Nvidia)[/COLOR]

Hope some of you can help me with this,
because after reading this thread and may more im no smarter then i was its still the 2 different opinions some say don't some say no problem and there is no mention if the new nvidia will work at all, 

with the new release of 10.04 i was hoping to get some new light in this subject.

---

### Post by blackmonjd on 2010-12-20
> **abhiroopb said:**
> I am planning on buying the HD5850. Would you say the support is good for it?
 
I have actually just started a thread about it here: [http://ubuntuforums.org/showthread.php?p=8802107#post8802107](http://ubuntuforums.org/showthread.php?p=8802107#post8802107)
 
I should have the computer by the end of next week. Where would I get the driver from? How would I update it? Would dual monitors work?
 
Currently using the 5850 with Ubuntu 10.04 (Lynx) and the 10.1 Catalyst Drivers.  Dual monitors will give you a wierd flicker.  It doesn't render the system unusable, but will make a few things annoying: scrolling, switching desktops in compiz, full screen on with any video or game (ie. World of Goo, youtube).
 
However, if you disable the second monitor during the times you don't need both, the problem is resolved. I have noticed that a small line sometimes appears and floats around with full screen videos, but it's random and doesn't always stick around.
 
Once again, the card is functional but you will run into some annoying issues.

---

