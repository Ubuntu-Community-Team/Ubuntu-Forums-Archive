---
title: "Ati X600se, 8.18.6 driver"
date: 2005-10-13
forum: Hardware &amp; Laptops
---

### Post by Marsupilami on 2005-10-13
Hi,

Any experience with these hardware and driver ?

(edit : X600se, sorry.)

Thx.

---

### Post by a2ps on 2005-10-13
finally ATI launched new linux drivers!
does it support the X600SE already? God i hope so!

still havent tried it, since im downloading Badger, i want to try it in a new clean and updated system.

---

### Post by Marsupilami on 2005-10-13
[QUOTE=a2ps]does it support the X600SE already? God i hope so!
[/QUOTE]
 
Found on the Ati web site in the [COLOR="Navy"]ATI Proprietary Linux Release Notes[/COLOR], [COLOR="DarkGreen"]ATI Mobility™ Product Support[/COLOR] :

[LIST]
[*]Mobility™ Radeon® X700
[*]Mobility™ Radeon® 9800
[*]Mobility™ Radeon® 9600
[*]Mobility™ Radeon® 9550
[*]Mobility™ Radeon® 9000
[*]Mobility™ Radeon® 9200
[*]Radeon® Xpress 200M series
[/LIST]

No X600 #-o 
I'm waiting for courageous pioneer before breaking my partitions :-\" :mrgreen:

---

### Post by a2ps on 2005-10-17
ok, its finally working!
just install the drivers the way you like (downloading from ati web site or using apt-get (on the repositories, the drivers arent yet 8.18.6, but they work too) lool).

then go to /etc/X11/xorg.conf
on the Device section, change driver from "ati" or "vesa" to "fglrx"
and add a line like this (still in the device section): ChipID 0x3150

is that easy! we could have done this 2 months ago!
well, better late then never..

the number 0x3150 is the chip id for the mobility x600, but works also for the x600se, since the difference its just the bus speed.

and dont worry, it still recognises the card as a x600se :P

a2ps@Miguel-Laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 SE Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

hehe, im getting 2700+ fps's on glxgears :)

---

### Post by Marsupilami on 2005-10-18
Thanks ! It works fine.

Only need to install of [COLOR="Sienna"]xorg-driver-fglrx[/COLOR] and then follow your instructions :D

---

### Post by mlomker on 2005-10-18
> and add a line like this (still in the device section): ChipID 0x3150


Out of curiousity--did it not work without the ChipID line?

---

### Post by Marsupilami on 2005-10-20
[QUOTE=mlomker]Out of curiousity--did it not work without the ChipID line?[/QUOTE]

I did not try with the last Ati driver but it does not work with one in the Breezy distrib.

---

### Post by mlomker on 2005-10-20
FYI, the Ubuntu developer in charge of the ATI drivers made a major breakthrough today. FGLRX is now fixed for 64-bit users. I'm going to have [my how-to's]("http://ubuntuforums.org/showthread.php?t=75382") updated as soon as I can generate the .deb files.

---

### Post by GoodPanos on 2005-10-21
Does this driver also work for the ATI Mobility Radeon X300?
What's the advantage of having the driver installed?

---

### Post by Marsupilami on 2005-10-25
> Does this driver also work for the ATI Mobility Radeon X300?
no idea sorry :( 

> What's the advantage of having the driver installed?
To benefit from all functionalities, 3D acceleration for example.

---

### Post by dekae on 2005-12-27
Hello, I've been trying to read this and other threads about getting my video card to work but I'm totally lost and I don't even know where to start. So far I did sudo dpkg-reconfigure xserver-xorg but it didn't work.

I have ATI Mobility Radeon X600 SE 64MB too. And when I try to start ubuntu then it tells me that there is an Error when it tries to start X server. My kernel is  2.6.12-10-386.
The errors are:
(EE) No devices detected
Fatal server error:
  No screens found

I hope someone can help me thank you.

---

### Post by dekae on 2005-12-27
I did what I found on [http://www.ubuntuforums.org/showthread.php?t=75378&highlight=screens](http://www.ubuntuforums.org/showthread.php?t=75378&highlight=screens) but still no luck.
```

sudo apt-get remove xorg-driver-fglrx
sudo apt-get remove linux-restricted-modules-$(uname -r)
sudo dpkg-reconfigure xserver-xorg #*Select the ATI driver*
reboot
sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #*Okay if it is already installed*
sudo dpkg-reconfigure xserver-xorg #*Select the fglrx driver*

```

when I tried to confirm if it had worked with fglrxinfo it showed
Error: unable to open display :0
??

---

### Post by mlomker on 2005-12-28
Did you do the ChipID part in post #4?  The driver didn't support the card in 8.18.x and I'm not sure if the latest one does, either.

/var/log/kern.log and Xorg.0.log have all of the error/log messages.

---

### Post by dekae on 2005-12-28
Ok, I followed your other HOW-TO and it works now. I'm so happy. Thank you

---

