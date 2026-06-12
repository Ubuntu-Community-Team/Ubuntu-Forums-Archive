---
title: "Ubuntu 11.04 and ATI Radeon HD 5145"
date: 2011-10-11
forum: Hardware
---

### Post by Ricardo_93 on 2011-10-11
Hi, i have a toshiba satellite L 650 and an ati radeon HD 5145, and after installing the OS, when I install the drivers that ubuntu want me to install in control panel, the desktop gets slower and the system says tah i have an ati radeon HD 4000 series...

Can anyone help me with this?

---

### Post by Darkling1991 on 2012-01-09
Hello, i have exactly the same problem, cannot display videos or games proparly because of this problem, have you solve it? Or anyone can help please?

---

### Post by cmileto on 2012-01-09
tried uninstalling the drivers and installing the propiatory drivers from ati?

---

### Post by MoreOrLess on 2012-01-09
Use the default open-source driver for best desktop performance. Don't install the proprietary driver.
BTW, the RadeonHD 5145 is a rebadged RadeonHD 46x0 GPU, so that's why it shows as a 4000...

---

### Post by Darkling1991 on 2012-01-10
> **MoreOrLess said:**
> Use the default open-source driver for best desktop performance. Don't install the proprietary driver.
BTW, the RadeonHD 5145 is a rebadged RadeonHD 46x0 GPU, so that's why it shows as a 4000...

It seems the open-source driver is the really the way to go :D video is working fine now and Ubuntu 11.04 desktop is working smooth too. Thanks a lot for the help ;) never tough the open-source driver was the solution

---

### Post by Mark Phelps on 2012-01-10
> **Darkling1991 said:**
> ... never tough the open-source driver was the solution

And for a long time, you were right...

But, the recent open-source drivers have made great strides -- to the degress that I no long bother with the restricted drivers.  The open-source drivers give me full resolution and multiple desktops.

---

### Post by Darkling1991 on 2012-01-18
> **Mark Phelps said:**
> ...the recent open-source drivers have made great strides -- to the degress that I no long bother with the restricted drivers.

So i assume i will have the full potencial of this graphic card in games (if someday i want to play something) with this drivers?

---

### Post by MoreOrLess on 2012-01-18
The proprietary driver is faster in 3D. Whether that makes enough of a difference depends on how demanding the game is.

---

### Post by Darkling1991 on 2012-02-01
> **MoreOrLess said:**
> The proprietary driver is faster in 3D. Whether that makes enough of a difference depends on how demanding the game is.

Drivers open-source are great for desktop and movies, but still they don´t use the full potencial of this card in games or other 3D programs. For what i tested so far i can´t have the 2 things...There is a way to put the propriatery drivers on 5145 for games and other 3D programs but still have great desktop and system perfomance (without lags on movies and windows)?

---

### Post by collisionystm on 2012-02-01
Install the driver from AMD if your card is supported.

install compizconfig settings manager

click OPENGL, disable sync to vblank, set texture filter to fast

if you have screen tearing enable tear free in catalyst.

the new amd driver is claiming to be "production ready" and will hopefully be packaged in 12.04

---

### Post by Darkling1991 on 2012-02-01
> **collisionystm said:**
> Install the driver from AMD if your card is supported.

install compizconfig settings manager

click OPENGL, disable sync to vblank, set texture filter to fast

if you have screen tearing enable tear free in catalyst.

the new amd driver is claiming to be "production ready" and will hopefully be packaged in 12.04

Thanks a lot!! Drivers 11.11 working like a charm :D

---

### Post by collisionystm on 2012-02-02
> **Darkling1991 said:**
> Thanks a lot!! Drivers 11.11 working like a charm :D

sweet!

Lets hope we dont have to hack ubuntu when 12.04 comes out lol.

Boy am I ready for an LTS.

---

