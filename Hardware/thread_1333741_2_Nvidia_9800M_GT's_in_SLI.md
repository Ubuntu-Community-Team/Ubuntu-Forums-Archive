---
title: "2 Nvidia 9800M GT's in SLI"
date: 2009-11-21
forum: Hardware
---

### Post by Diod on 2009-11-21
I have a laptop running Xubuntu 9.10 with 2 9800M GT's that I wanna put in SLI. I'm running driver version 185.18.36
I've tried adding the SLI option in the xorg.conf file, but when I would restart my laptop, I would get a black screen.
I have also tried adding the BusID to the device section, but it would still result in a black screen.

By black screen i mean that it appeared as if the screen was completely turned off. (in contrast to the screen being on and showing black)

Any clues on how to get SLI working?

---

### Post by Diod on 2009-11-23
*bump*

---

### Post by Martins2040 on 2010-02-05
> **Diod said:**
> I have a laptop running Xubuntu 9.10 with 2 9800M GT's that I wanna put in SLI. I'm running driver version 185.18.36
I've tried adding the SLI option in the xorg.conf file, but when I would restart my laptop, I would get a black screen.
I have also tried adding the BusID to the device section, but it would still result in a black screen.

By black screen i mean that it appeared as if the screen was completely turned off. (in contrast to the screen being on and showing black)

Any clues on how to get SLI working?

Are you having 3 total cards?

Like i have 1x9400M 2x9800M GTS

Im still working on getting Ubuntu 9.10 to like those 2x9800M GTS, but still no luck.

Try run: lspci

I get:
02:00.0 VGA compatible controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
03:00.0 3D controller: nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
04:00.0 VGA compatible controller: nVidia Corporation C79 [GeForce 9400M G] (rev b1)

---

### Post by Diod on 2010-02-06
lspci gives me:

> 03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800M GT] (rev a2)
04:00.0 3D controller: nVidia Corporation G92 [GeForce 9800M GT] (rev a2)


Anyway, I've uninstalled xubuntu and installed Arch Linux a few days ago. I haven't tried SLI yet, but I'm gonna do that today. It's probably not gonna make a difference, but who knows :)

EDIT: I can enable SLI, but it slows down anything that requires output to my screen(as in window creation, ...). It seems to hang for a little while when creating a window for example. Eventually it does create the window, but it takes a lot of time. This is running v190.53 of the nvidia drivers that are in Arch Linux' repositories.

---

