---
title: "Intel G965 driver package"
date: 2007-08-12
forum: Hardware &amp; Laptops
---

### Post by kkjaergaard on 2007-08-12
I've got a laptop with the Intel G956 chipset, but I can't find a graphics driver package for it.

Do I have to recompile the kernel to use my screen's 1440x900 resolution, or is there a driver package somewhere?

- I'm not used to Linux...

---

### Post by davidmorawski on 2007-08-12
I'm not a doctor, but you may want to try the following:
```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install-xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg
```
Depending on your GMA, you may need an additional driver. [Here's]("http://ubuntuforums.org/showthread.php?t=494943") one for the x3100.
Also, changing the Driver to "intel" under the "Device" section in your xorg.conf may be in order.

Good luck,

Dave

---

### Post by Matt Yun on 2007-08-12
You do not need to recompile anything.  However, you will need the Intel driver package.  From a console, do the following:

```
sudo apt-get update && sudo apt-get install xserver-xorg-video-intel
sudo dpkg-reconfigure xserver-xorg

```

After you do dpkg-reconfigure, you will go through various text dialog boxes.  Choose all defaults, except pick 'intel' as your driver, and 1440x900 as your resolution.

See this thread for more help:  [1280X800 on [Dell] 640m]("http://ubuntuforums.org/showthread.php?t=473552").

---

### Post by kkjaergaard on 2007-08-12
> **davidmorawski said:**
> 
```

...
sudo apt-get install-xserver-xorg-video-intel
...

```

Depending on your GMA, you may need an additional driver. [Here's]("http://ubuntuforums.org/showthread.php?t=494943") one for the x3100.

I have that package, but current stable xserver-xorg-video-intel doesn't contain drivers for the 965 chipset (it contains almost any other older driver for Intel chipsets).

Thanks for the guide. My GMA is X3000 (not X3100 as the guide targets) but I'll try it anyway.

---

### Post by CC_machine on 2007-08-12
on my laptop with the intel 945G chipset, i used package "915resolution" to fix my screenres from 1024x768 -> 1280x800. not sure if it works on the new x3100, but try it :p

---

### Post by kkjaergaard on 2007-08-13
> **CC_machine said:**
> on my laptop with the intel 945G chipset, i used package "915resolution" to fix my screenres from 1024x768 -> 1280x800. not sure if it works on the new x3100, but try it :p

It doesn't work - I've tried it. I don't think it works on chipsets newer than 945G.

---

### Post by kkjaergaard on 2007-08-13
> **davidmorawski said:**
> Depending on your GMA, you may need an additional driver. [Here's one for the x3100.]("http://ubuntuforums.org/showthread.php?t=494943")


Great, this works. By the way, why isn't that package in the reposities?

---

