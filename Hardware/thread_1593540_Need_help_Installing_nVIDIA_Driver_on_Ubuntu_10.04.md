---
title: "Need help Installing nVIDIA Driver on Ubuntu 10.04 LTS 64bit"
date: 2010-10-11
forum: Hardware
---

### Post by r352alit on 2010-10-11
Hi.... It's me, again... i hope you guys doesn't bored with me.

I've just finish installing Ubuntu 10.04 LTS 64 bit, and... same as always on every new Ubuntu version, i can't install the graphic driver.
I just downloaded from nvidia.com the driver version for 64 bit (NVIDIA-Linux-x86_64-256.53.run) and try to install it. Normally using sh NVIDIA-Linux-x86_64-256.53.run

But before go to that command line, i've use this line : sudo etc/init.d/gdm stop command line, but then appear error on the tty1 that i've should use stop gdm rather than using command init.d/gdm stop. 

I've already searching on the ubuntu documentation, but so far.... nothing... 

So am i using the "right one" or did i miss something here...?
can anyone help... i need some enlightment, sorry for the trouble and thank you....

---

### Post by ubunterooster on 2010-10-11
We don't get easily bored. :D

Your computer is saying it does not like the command ```
sudo etc/init.d/gdm stop
```It wants you to run```
sudo stop gdm

```

---

### Post by shreepads on 2011-01-13
If its not too late or for anyone else who lands up here, please have a look at this:

[http://ubuntuforums.org/showthread.php?t=1665630](http://ubuntuforums.org/showthread.php?t=1665630)

---

