---
title: "K8M800 embedded graphics drivers - please advice"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by wpginfo on 2008-03-23
Hallo,

I would greatly appreciate your help with the following.
I am a NEWBIE trying to run UBUNTU 7.10 on a K8M800 based machine.
I ran a default installation and installed all of the suggested updates
For some reason it won't run my graphics beyond 800*600, while my monitor (and MBoard?) can.
This spoils my web-experience quite a lot.
Please advice WHAT to do, and HOW to do it.

---

### Post by overdrank on 2008-03-23
> **wpginfo said:**
> Hallo,

I would greatly appreciate your help with the following.
I am a NEWBIE trying to run UBUNTU 7.10 on a K8M800 based machine.
I ran a default installation and installed all of the suggested updates
For some reason it won't run my graphics beyond 800*600, while my monitor (and MBoard?) can.
This spoils my web-experience quite a lot.
Please advice WHAT to do, and HOW to do it.

HI and welcome, what is the model of the graphics chipset? You can find this with the command lspci in the terminal located under applications, accessories. Look for VGA. Then you may reconfigure your xorg with this command ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by wpginfo on 2008-03-28
Hello Overdrank,

Thank you for your advice.
My MBrd has a VIA graphics chipset  vt8237r embedded.
Ubuntu installed the via unichrome drivers.
The monitpr is a LG Studioworks 550M
Unfortunately this combination works well in HiRes under windows, but still doesn't work under ubuntu, despite your suggestion.
I tested the system usuing a hires lcd screen. It worked fine! So the MB chipset works.
Perhaps there are other ways to solve this? Or is a different screen the only way out?

---

### Post by sriramoman on 2008-04-25
Goto System-->Preferences-->Screen Resolution and try the best refresh rate+resolution combination.
The combination is important, as you may get black screens at particular refresh rates, even with the recommended resolution.

---

### Post by darkwalt on 2008-05-03
Yeah, I have the same mobo, and this is my first install.  The problem that i'm having is that the resolution goes from 640x480 straight to 1600x1200.  Is there a way to unlock all of the resolutions between that and get it all fitting within the monitor so I won't have to scroll across the desktop?

---

