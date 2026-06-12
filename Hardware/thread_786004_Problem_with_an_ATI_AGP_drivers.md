---
title: "Problem with an ATI AGP drivers"
date: 2008-05-07
forum: Hardware
---

### Post by fidoda on 2008-05-07
Hi, I have an ATI AGP and the problem is not installing the drivers but rather after rebooting. Just after the restricted drivers have installed I reboot, see the Ubuntu loading logo and then.. nothing, black screen.

I have an ATI AGP x1650 512mb DDR2 PowerColor on Ubuntu 8.04 for "normal PCs" (x86 I think).

Thx for helping me!

---

### Post by Rocket2DMn on 2008-05-07
You can reboot into the recovery mode kernel (the second option and GRUB menu) and run
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Let the system reboot normally, now you should get back into the GUI with the original install settings.  Remove the restricted drivers with
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then try using EnvyNG to download and install the correct restricted drivers - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)

---

### Post by juansjc on 2008-05-07
> **Rocket2DMn said:**
> You can reboot into the recovery mode kernel (the second option and GRUB menu) and run
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```
Let the system reboot normally, now you should get back into the GUI with the original install settings.  Remove the restricted drivers with
```
sudo apt-get remove --purge xorg-driver-fglrx
```
Then try using EnvyNG to download and install the correct restricted drivers - [http://www.albertomilone.com/envyngfaq.html#A](http://www.albertomilone.com/envyngfaq.html#A)


[B]Wow this a good solution:lolflag:

BUT, how install driver for x1650 AGP?[/B]:confused:
my desktop: Abit NF7 with nForce 2 with Athlon XP + **ATI X1650 AGP**

---

### Post by Rocket2DMn on 2008-05-07
> **juansjc said:**
> [B]Wow this a good solution:lolflag:

BUT, how install driver for x1650 AGP?[/B]:confused:
my desktop: Abit NF7 with nForce 2 with Athlon XP + **ATI X1650 AGP**

Funny.  EnvyNG will install restricted drivers for you, just click the link in my last post, it gives you directions.

---

### Post by fidoda on 2008-05-07
It did not work. Still have the same problem.:confused:

---

### Post by Rocket2DMn on 2008-05-08
Some research shows that your card is compatible with the radeonhd driver.  So here's how we're going to try and install it.  I will first have you enable the fallback "vesa" video driver.  Reboot again into the recovery mode kernel and run (with the capital X in X11)
```
nano /etc/X11/xorg.conf
```
Scroll down to where it says
```
Section "Device"
     Identifier "Configured Video Device"
EndSection
```
and add a new line to make it look like this
```
Section "Device"
     Identifier "Configured Video Device"
     Driver "vesa"
EndSection
```
Do CTRL+X to get out, press Y and Enter to save and get out, then reboot
```
reboot
```
You should now be able to log into the GUI after a normal reboot, though the graphics may look terrible.  Open a terminal and run
```
sudo apt-get install xserver-xorg-video-radeonhd
```
Now open xorg.conf for editing again
```
gksudo gedit /etc/X11/xorg.conf
```
At the bottom add
```
Section "Extensions"
Option "Composite" "Off"
EndSection

Section "ServerFlags"
Option "AIGLX" "Off"
EndSection
```
and change the "vesa" in the file to "radeonhd"
Save and close.  Now to CTRL+ALT+BACKSPACE to restart X.  Hopefully this should get you a decent setup.

---

### Post by sackbj on 2008-05-08
I didn't see a pertinent thread to this question on the first couple pages of the forum, but this is a related question:

Nvidia products generally work better with Linux - is this correct?

I have a machine with an old Nvidia 6800 that is running Ubuntu right now, and it works very well for me.  Installing the restricted drivers went pretty well without having to use Envy.

My newer machine has an ATI Sapphire HD 3870 X2.  I have thought about installing Ubuntu on this machine as well.  Would I still be able to make use of compiz effects and play DVD's and video at decent rates?

---

### Post by Rocket2DMn on 2008-05-08
> **sackbj said:**
> I didn't see a pertinent thread to this question on the first couple pages of the forum, but this is a related question:

Nvidia products generally work better with Linux - is this correct?

I have a machine with an old Nvidia 6800 that is running Ubuntu right now, and it works very well for me.  Installing the restricted drivers went pretty well without having to use Envy.

My newer machine has an ATI Sapphire HD 3870 X2.  I have thought about installing Ubuntu on this machine as well.  Would I still be able to make use of compiz effects and play DVD's and video at decent rates?

I can't say for sure, I'm not well versed on the compatibility of Radeon HD cards, I think it might be lagging a bit.  You can google around some more, but there probably isn't much info on it because the card is so new and Hardy hasn't been out long.

---

### Post by lifve on 2008-05-08
I have similar problem. I use Ati Radeon Xpress 200M.
the visual looks better after Installed restricted driver. I can use the effect now.
but when I play video, it worse than before install restricted driver.
the driver I get from ubuntu packages.
so now I'm turn back to original. but the effect can't show.
well, I don't really bother with this, because the video plays well.
just, I'm curious, after I visit ATI driver page, it gives spesific driver for my graphic card. ATI radeon xpress 200m linux x86_64 driver. I use Hardy for AMD64.
but I can't install it. after I click twice, it shows gedit can't read the code something.
so somebody may have solution for this? how to install it? should I install it?
thanks.

---

### Post by benevolent on 2008-05-08
> **fidoda said:**
> Hi, I have an ATI AGP and the problem is not installing the drivers but rather after rebooting. Just after the restricted drivers have installed I reboot, see the Ubuntu loading logo and then.. nothing, black screen.


Same thing happens here (with X1650PRO AGP - 256Mb)


I try installing drivers via envyng, but I get blank screen again...



to fix it, i just boot recovery mode and uninstalled the drivers with envyng -t



Any help????

---

### Post by fidoda on 2008-05-08
I just did what you said. No black screen when booting but I can't enable compiz. Is that normal?

---

### Post by fidoda on 2008-05-08
bump

---

### Post by Rocket2DMn on 2008-05-08
To who's post are you referring?
Other people have been having problems with the x1650 card, so you are not alone.  Why don't you try installing the radeonhd driver, it should be compatible with your card.
```
sudo apt-get install xserver-xorg-video-radeonhd
```

---

### Post by fidoda on 2008-05-09
> **Rocket2DMn said:**
> To who's post are you referring?
Other people have been having problems with the x1650 card, so you are not alone.  Why don't you try installing the radeonhd driver, it should be compatible with your card.
```
sudo apt-get install xserver-xorg-video-radeonhd
```

This is what I did. But I can't enable compiz.

---

### Post by Rocket2DMn on 2008-05-09
> **fidoda said:**
> This is what I did. But I can't enable compiz.

It looks like somebody else already reported a bug for your card with similar problems, so it may be that you can't run Compiz for now
[https://bugs.launchpad.net/baltix/+source/linux-restricted-modules-2.6.24/+bug/198803](https://bugs.launchpad.net/baltix/+source/linux-restricted-modules-2.6.24/+bug/198803)
I would make a post on that bug report (you will need to register on Launchpad) and give them any details you can.  This can help them confirm and bug and hopefully release a fix for it.

---

### Post by benevolent on 2008-05-10
> **Rocket2DMn said:**
> To who's post are you referring?
Other people have been having problems with the x1650 card, so you are not alone.  Why don't you try installing the radeonhd driver, it should be compatible with your card.
```
sudo apt-get install xserver-xorg-video-radeonhd
```


I did that and solved this problem:

[[img]http://img216.imageshack.us/img216/8597/ubuiy1.th.png[/img]](http://img216.imageshack.us/my.php?image=ubuiy1.png)


but still no 3d acceleration :(


thx anyway :)

---

### Post by BorisK on 2008-05-10
> **sackbj said:**
> I didn't see a pertinent thread to this question on the first couple pages of the forum, but this is a related question:

Nvidia products generally work better with Linux - is this correct?

I have a machine with an old Nvidia 6800 that is running Ubuntu right now, and it works very well for me.  Installing the restricted drivers went pretty well without having to use Envy.

My newer machine has an ATI Sapphire HD 3870 X2.  I have thought about installing Ubuntu on this machine as well.  Would I still be able to make use of compiz effects and play DVD's and video at decent rates?

About the HD 3870 X2 : It's a possibility that fglrx will freeze your comp on boot, like it did with my AGP HD2600Pro. 8.3 and 8.4 fglrx worked, but previous versions didn't. I think it still doesn't work for some people. You should wait for a few more fglrx releases.

---

### Post by fidoda on 2008-05-12
When I try to enable special effects I got a white screen. The cursor is still visible.

---

### Post by patejl69 on 2008-05-18
Anyone who is getting black screen with ATI try increasing AGP aperture size in BIOS...it helped me, system run, fglrxinfo shows ATI glxinfo shows Direct Rendering but GXLGEARS shows BLACK SCREEN and framerate...if anyone can tell me why i would be happy!

---

