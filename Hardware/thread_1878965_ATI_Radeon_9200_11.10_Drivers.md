---
title: "ATI Radeon 9200 11.10 Drivers"
date: 2011-11-10
forum: Hardware
---

### Post by ngloxo72 on 2011-11-10
hi! I'm Trying to install the ATI drivers for Ubuntu 11.10 from the ATI website and I do this:
[IMG]http://imgur.com/3DpUz[/IMG]

It then goes on to do this:
[IMG]http://imgur.com/3m4mH[/IMG]

The full log is here:

ngloxo@ngloxo-DM038A-ABU-t250-uk:~$ cd /home/ngloxo/Downloads
ngloxo@ngloxo-DM038A-ABU-t250-uk:~/Downloads$ sudo sh ati-driver-installer-8.28.8.run --buildpkg Ubuntu/maverick
Creating directory fglrx-install
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.28.8.....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
-e ==================================================
-e  ATI Technologies Linux Driver Installer/Packager 
-e ==================================================
Generating package: Ubuntu/maverick
Requested package is not supported.
Removing temporary directory: fglrx-install
-----------------------------------------------------------------------------------
Can you pleas help me?

EDIT: the pics dont work!
Also If I click Additional Drivers, it looks for drivers then tells me that no Propiretey Drivers are installed. and there isnt a box for enabling them.

01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200] (rev 01)

---

### Post by overdrank on 2011-11-10
Hi and welcome, as the terminal shows it is not supported. ATI dropped support for those models sometime ago. :)

---

### Post by mastablasta on 2011-11-11
you are stuck with opensource drivers. 
 
to upgrade the opensource ones with development version you would need to add a PPA to it. 
Instructions on how to do that and what it brings tothe OS (READ THEM FIRST) and the PPA itself are found here: 
[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)
--
 
also is there a special reason you were trying to install proprietary ATI drivers?

---

### Post by BillyBoa on 2011-11-11
> **mastablasta said:**
> also is there a special reason you were trying to install proprietary ATI drivers?

I think there is a very special reason. 
The opensource drivers cause computer fan to run like a Jumbo Jet during take of and battery life is decreasing a lot. 


It's due to the bug Bug #563156

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/563156)

---

### Post by khelben1979 on 2011-11-11
To me it looks like you need to go back and install [Ubuntu 9.04]("http://en.wikipedia.org/wiki/Ubuntu_9.04_jaunty_jackalope#Ubuntu_9.04_.28Jaunty_Jackalope.29") if you need the non-free ATi drivers working, so it's either that or,

use the open source ATi/AMD video drivers. Changes in the X server makes the older video drivers not working any more. I'm stuck myself on an older version of my distribution for the same reason, keep in mind though that you can use modern software any way, but it requires some... more technical skills than usual to get it working, it might even include compiling from source...

---

### Post by MoreOrLess on 2011-11-11
> **khelben1979 said:**
> To me it looks like you need to go back and install [Ubuntu 9.04]("http://en.wikipedia.org/wiki/Ubuntu_9.04_jaunty_jackalope#Ubuntu_9.04_.28Jaunty_Jackalope.29") if you need the non-free ATi drivers working
That's for r300 (Radeon 9500 or later) cards or later. The Radeon 9200 is an r200-based card which only runs with fglrx 8.28 (which only runs on Ubuntu 6.06 and earlier).

---

### Post by MoreOrLess on 2011-11-11
> **khelben1979 said:**
> To me it looks like you need to go back and install [Ubuntu 9.04]("http://en.wikipedia.org/wiki/Ubuntu_9.04_jaunty_jackalope#Ubuntu_9.04_.28Jaunty_Jackalope.29") if you need the non-free ATi drivers working
That's for r300 (Radeon 9500 or later) cards or later (and 9.04 is not supported anyway). The Radeon 9200 is an r200-based card which only runs with fglrx 8.28 (which only runs on Ubuntu 6.10 and earlier). For the older card, the open-source driver is still making improvements, and I recommend using xorg-edgers PPA.

---

### Post by khelben1979 on 2011-11-11
> **MoreOrLess said:**
> The Radeon 9200 is an r200-based card which only runs with fglrx 8.28 (which only runs on Ubuntu 6.10 and earlier).

Thanks for pointing that out! I was hoping that it would include the whole series of Radeon 9000 cards..

---

