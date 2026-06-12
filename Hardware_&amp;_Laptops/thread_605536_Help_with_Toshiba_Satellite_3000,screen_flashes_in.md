---
title: "Help with Toshiba Satellite 3000,screen flashes in various colours,blanked."
date: 2007-11-07
forum: Hardware &amp; Laptops
---

### Post by yujin1984320 on 2007-11-07
OK,guys, i'm totally new to Ubuntu,and i don't know what is gusty,and fiesty...........
i just downloaded the version on the Ubuntu homepage, the LiveCD version, it runs on my desktop smoothly,but i decided to install that on my old laptop, which is toshiba satellite 3000 with nvidia GeForce2 Go card onboard. i just run through the CD, after Ubuntu loaded, the screen turns into another colour, and flashing in random colour later on, i don't know what to do.
i did some search said the nvidia GeForce2 Go card need legacy driver, but without proper display, how can i install that.

and i noticed on the boot menu, there is an option, install from driver update CD, what is it.

Thx for reading that, and i hope someone can help me.
PS. Ubuntu is a stunning OS.
Cheers!

---

### Post by mpierce on 2007-11-07
You are going to have to install the legacy drivers from the terminal. 
When you login which you can't select ctrl+f1 to go to a terminal.

You will then have to install the legacy drivers by doing:
1) dpkg -l | grep nvidia
   this will tell you which nvidia packages are installed.
2) you will need to have the following packages.
   nvidia-glx-legacy
   nvidia-kernel-common
   nvidia-xconfig (optional)
3) sudo apt-get install nvidia-glx-legacy nvidia-kernel-common nvidia-xconfig
   it will tell you that you are downgrading, select Y(es) when asked.

As you are a newbie reboot and all should be well.

Hope this helps...

---

