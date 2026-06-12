---
title: "Kernal Changes"
date: 2009-06-28
forum: Installation &amp; Upgrades
---

### Post by zoomy942 on 2009-06-28
So i read online on the Launchpad that my intel HD controller has a bug that creates corrupt file systems on jaunty 64bit.  that being said 2.6.29 was suipposed to make things alot smoother.  I installed it and now i dont know how to remove the old ones with command line.  anyone shed some light?  

```
zimmerman@zimmerman-laptop:~$ uname -a
Linux zimmerman-laptop 2.6.29-02062905-generic #02062905 SMP Tue Jun 16 09:04:31 UTC 2009 x86_64 GNU/Linux

```

```
zimmerman@zimmerman-laptop:~$ dpkg -l | grep linux-headers-*
ii  linux-headers-2.6.28-13                    2.6.28-13.44                              Header files related to Linux kernel version
ii  linux-headers-2.6.28-13-generic            2.6.28-13.44                              Linux kernel headers for version 2.6.28 on x
ii  linux-headers-2.6.29-020629                2.6.29-020629                             Header files related to Linux kernel version
ii  linux-headers-2.6.29-020629-generic        2.6.29-020629                             Linux kernel headers for version 2.6.29 on x
ii  linux-headers-2.6.29-02062905              2.6.29-02062905                           Header files related to Linux kernel version
iF  linux-headers-2.6.29-02062905-generic      2.6.29-02062905                           Linux kernel headers for version 2.6.29 on x
ii  linux-headers-generic                      2.6.28.13.17                              Generic Linux kernel headers
zimmerman@zimmerman-laptop:~$ 

```

---

### Post by cariboo on 2009-06-28
Why not just use Synaptic Package Manager to remove the extra kernels?

---

### Post by zoomy942 on 2009-06-28
honestlybecasue when i searched for it i didnt see it

---

### Post by zoomy942 on 2009-06-29
so far this kernel has been rock solid.  just havent removed the old ones yet.

---

### Post by moster on 2009-06-29
> **zoomy942 said:**
> honestlybecasue when i searched for it i didnt see it

buddy, what is name of that skin and where you get it? Sorry, I do not know anything about deleting kernels..

---

### Post by zoomy942 on 2009-06-29
> **moster said:**
> buddy, what is name of that skin and where you get it? Sorry, I do not know anything about deleting kernels..

here ya go

[http://www.ubuntugeek.com/nice-ubuntu-themes-for-jaunty-and-intrepid-users.html]("http://www.ubuntugeek.com/nice-ubuntu-themes-for-jaunty-and-intrepid-users.html")

---

### Post by moster on 2009-06-29
Oh, I did not know for these. Beautiful, thanks :)

---

