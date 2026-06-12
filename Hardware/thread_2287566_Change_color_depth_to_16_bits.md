---
title: "Change color depth to 16 bits"
date: 2015-07-20
forum: Hardware
---

### Post by cpcbegin-hotmail on 2015-07-20
I need momentarily change the screen resolution to a color depth of 16 bits, to run [this]("https://github.com/KaosOverride/CapriceRPI")[ Amstrad CPC emulator]("https://github.com/KaosOverride/CapriceRPI") than requires 16 bits color to run.

 I've been looking for some documentation about xrandr but I have found nothing to do this.
 The idea is to create a script with three instructions: put the color depth to 16-bit, run the program and when finished return to color depth previous value.
 My graphics card is a NVIDIA Corporation GF119 [GeForce GT 610] (rev a1)

The program is for Raspberry pi but when I compile it successfully on Ubuntu 14.04 64 bits and Lubuntu 14.04 32 bits but, in both cases, shows this error:
```
Mode not available.
Caprice needs 16bpp. System is in 32bpp
video_init() failed. Aborting.
```

---

### Post by dino99 on 2015-07-21
it should still works

[http://ubuntuforums.org/showthread.php?t=1545608](http://ubuntuforums.org/showthread.php?t=1545608)

---

### Post by cpcbegin-hotmail on 2015-07-22
> **dino99 said:**
> it should still works

[http://ubuntuforums.org/showthread.php?t=1545608](http://ubuntuforums.org/showthread.php?t=1545608)

Thanks, but there is no /etc/X11/xorg.conf file.

---

### Post by sudodus on 2015-07-22
You can create it with a text editor in a terminal window (copy and paste to make it like what is shown in the link).

```
sudo nano /etc/X11/xorg.conf
```

---

