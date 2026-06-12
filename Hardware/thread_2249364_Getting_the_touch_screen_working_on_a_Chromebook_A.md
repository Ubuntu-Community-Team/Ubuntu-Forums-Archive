---
title: "Getting the touch screen working on a Chromebook Acer c720p"
date: 2014-10-21
forum: Hardware
---

### Post by damien15 on 2014-10-21
Hello everyone !

I've a big issue trying to get the touchscreen working on my Acer c720p. 

The last two weeks, I used ubuntu with crouton and I still had Chrome OS installed on my laptop. But to save space, I decided to entirely remove chrome OS and to install a fresh Ubuntu distribution. I installed ubuntu 14.04 64 bits with Unity.

It works perfectly except two things : the touchpad and the touchscreen. I achived getting the touchpad working by using this tutorial : [http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04](http://blog.jdpfu.com/2014/04/18/easy-acer-c720-ubuntu-14-04). Then, I used this tutorial to set up the sensitivity : [https://wiki.archlinux.org/index.php/Acer_C720_Chromebook](https://wiki.archlinux.org/index.php/Acer_C720_Chromebook).
Thanks to that, the touchpad works perfectly but I can't get the touchscreen working.

I don't know how to fix it. Has someone already done that ?

Thanks for your answers,

Damien.

(PS: I'm sorry for my poor english)

---

### Post by ferry_toth on 2014-10-23
For 14.04 I went here: [https://github.com/visionect/c720p](https://github.com/visionect/c720p)
But take care this involves building kernel modules.

The first kernel take will out of the box make the touchpad work as well as the touchscreen (with some small hickups, when it doesn't work, close the lid to suspend, then wake it up again, the touch screen should then work) is 3.17. You can get this from 'kernel ppa' and then use 'sudo dpkg -i linux-....' to get it installed.

Unfortunately, 14.10 uses 3.16 so that will not work. The patched drivers will probably not build for 3.16, so will either need to downgrade the kernel to 3.13 and build the drivers or upgrade to 3.17.

BTW Myself just upgraded to 14.10 and running kernel 3.17 now (C720P)

---

### Post by damien15 on 2014-11-02
Ok, thank you for the answer !
I will try to install the last kernel !

---

### Post by damien15 on 2014-11-03
Hello !

I tried to install the kernel 3.17 following this tutorial :
 [http://ubuntuhandbook.org/index.php/2014/10/install-upgrade-kernel-3-17-ubuntu/](http://ubuntuhandbook.org/index.php/2014/10/install-upgrade-kernel-3-17-ubuntu/)

It worked perfectly for me. Now, I've a totally functionnal install of Ubuntu 14.04.

Thanks you for your answer.

---

