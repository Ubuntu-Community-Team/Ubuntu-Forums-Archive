---
title: "How install video card drivers (i945, 8400, 3650) for 20.04 and 21.04 ?"
date: 2021-09-13
forum: Hardware
---

### Post by aug7744 on 2021-09-13
I want install Ubuntu 20.04 or 21.04 in computer with the video cards below :

Integrated
- Intel i945
- Intel the name I not remember exactly , but is more or less has 4 numbers iXXXX and is more fast than i945.

Discrete PCI-E
- Radeon HD 3650 512 MB
- Nvidia GeForce 8400 GS 512 MB

In additional drivers control panel not is displayed the gpus above.

Thanks for your reply.

---

### Post by Frogs Hair on 2021-09-13
Hello aug7744,

I had to retire my 8400GS because the proprietary nvidia 304 driver was removed from the repository some years ago. Is the card working with the open source driver ?

---

### Post by aug7744 on 2021-09-14
"I had to retire my 8400GS because the proprietary nvidia 304 driver was  removed from the repository some years ago. Is the card working with the  open source driver ?"
Not information to say here.

Perhaps using nvidia binary driver and correct dependencies will install GF 8400 , but I want install Intel GMA and Radeon HD 3650.
The video driver had to be more simple to install for legacy devices thus more users will switch to Linux , but has users that avoid a long time trying figure when not is possible any information direct about it.

---

### Post by mastablasta on 2021-09-14
Integrated
- Intel i945 [COLOR=#ff0000]-- driver is part of Linux Kernel. No additional install is needed.[/COLOR]
- Intel the name I not remember exactly , but is more or less has 4 numbers iXXXX and is more fast than i945. [COLOR=#ff0000]-- driver is part of Linux Kernel. No additional install is needed.[/COLOR]

Discrete PCI-E
- Radeon HD 3650 512 MB [COLOR=#ff0000]-- opensource radeon driver is part of Linux Kernel. No additional install is needed. Proprietary AMD driver is no longer supported since version 14.04.[/COLOR] 
- Nvidia GeForce 8400 GS 512 MB [COLOR=#ff0000]-- opensource nouvau driver is part of Linux Kernel. No additional install is available. Proprietary Nvidia driver is no longer avaialble as the chip fell out of legacy support (i.e. nvidia no longer provides driver for it) [/COLOR]

get a new card if you need more power. nvidia GT1030 would do and is much faster than your current selection. has closed source driver support (if you need it).
note that intel has all driver opensourced. they help with development and integration to kernel. AMD does so too but started doing that at a later date. so support for latest cards is good, for older ones is maybe not so good (missing features). more on features here: [https://www.x.org/wiki/RadeonFeature/](https://www.x.org/wiki/RadeonFeature/)

---

### Post by aug7744 on 2021-09-15
The machines are Celeron D , Phenom and another Intel mobile cpu being tested only a new installation in 2 machines and when accessing Additional Drivers Control Panel all information areas are empty not displaying any information about intel , Radeon HD 3650 or GF8400.
Thus I not understand if the OS is having correct OpenGL and graphics acceleration.

---

### Post by Yellow Pasque on 2021-09-15
Well, then they don't need **additional** drivers..

---

### Post by mastablasta on 2021-09-16
> **aug7744 said:**
> The machines are Celeron D , Phenom and another Intel mobile cpu being tested only a new installation in 2 machines and when accessing Additional Drivers Control Panel all information areas are empty not displaying any information about intel , Radeon HD 3650 or GF8400.
Thus I not understand if the OS is having correct OpenGL and graphics acceleration.


it means all available drivers are already in kernel and there are no available additional drivers.

i had HD3650 and i know it works quite well on linux with radeon driver.

---

### Post by aug7744 on 2021-09-17
I had installed Ubuntu 20.04 in 2 machines (GF 6100 and Radeon HD 3650).
The OS had started correctly , but the screen is full of flickering in fonts with areas using wrong colors or darker.

---

### Post by mikewhatever on 2021-09-17
> **aug7744 said:**
> I had installed Ubuntu 20.04 in 2 machines (GF 6100 and Radeon HD 3650).
The OS had started correctly , but the screen is full of flickering in fonts with areas using wrong colors or darker.

Those two are very old - years 2004 and 2008 respectively. Try something like Xubuntu or Lubuntu with 3d effects disabled, instead of Ubuntu. 
They might work a bit better, but I would consider a late retirement for both PCs.

...and just to make sure, there is no proprietary driver for either of those.

---

### Post by mastablasta on 2021-09-17
at login select xorg instead of wayland.

or try a distro like Kubutnu or Xubuntu that uses xorg.

@mikewhatever - they are old but they have 512 MB ram which is plenty to run just the desktop. i know for a fact Kubuntu 18.04 worked very well even with effects enabled. the Plasma KDE in 20.04 is even more optimised.

---

