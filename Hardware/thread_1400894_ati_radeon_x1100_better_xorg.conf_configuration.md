---
title: "ati radeon x1100 better xorg.conf configuration"
date: 2010-02-07
forum: Hardware
---

### Post by Rob6 on 2010-02-07
Hi! I have Ubuntu 9.10 and ATI radeon x1100 video card. I installed xf86-video-ati driver successfully. In xorg.conf i put Driver "ati" then i tried "radeon" - they both work but in some applications or games 3d works slower than in others. Which options are better for my card? Maybe someone can give me his xorg.coonf file if he has x1100card...            And one more thing: apps like google earth are not working properly - if there are dialog windows they are covered by 3d. i attached screenshot and my xorg.conf. Please help!...

---

### Post by Rob6 on 2010-02-08
Please help...

---

### Post by realzippy on 2010-02-08
Think ati and radeon is the same...:

*Driver specifies which driver you want to use. IT HAS TO BE ati and NOT radeon  or fglrx. The "ati" driver is a wrapper that will load the "radeon" driver if possible*

from:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Edit:...if you want full 3d hardware acceleration you had to install ubuntu 8.10 and the ATI Catalyst driver 9.3...since Ubuntu 9.04 it does not support your card anymore.

---

### Post by Rob6 on 2010-02-09
It cant be that no one knows how to solve these problems No answers..........!:-s

---

### Post by realzippy on 2010-02-10
I gave an answer.
Install 8.10 if you want "full" 3D with ATI.
Or live with the free driver you already use.

---

### Post by Rob6 on 2010-02-10
> **realzippy said:**
> I gave an answer.
Install 8.10 if you want "full" 3D with ATI.
Or live with the free driver you already use.
_I know this all that u've said_. But for example in alt linux and mandriva i had full 3d acceleration without proprietary closed-source ati driver. there was "radeon" in field Driver. I tried this driver in ubutnu that didn't work so fast as in those linuxes!!:neutral:

---

