---
title: "cannot locate kernel headers"
date: 2009-09-18
forum: Hardware
---

### Post by jimmybarcelona on 2009-09-18
been at this one for 2 days now, and it's starting to wear on me. I've downloaded the nvidia 173 driver straight from nvidia.com, but when I try to run the installer it cannot find the correct headers for my kernel. 
output of 'uname -r' is '2.6.28-3-rt'. So I downloaded linux-headers-$(uname -r) and there are now 2 folders in my /usr/src directory: linux-rt-headers-2.6.28-3-rt and linux-headers-2.6.28-3-rt. So I have the headers. Whenever I run the nvidia installer, it says that "file version.h does not exist. This is most likely because your kernel source files have not been configured." Basically the installer fails to build an nvidia kernel. I even used apt to download nvidia-173-kernel-source and it wouldn't let me compile that either because it can't work with my headers.
What now?

---

### Post by hal10000 on 2009-09-18
If you are on ubuntu 9.04 then just run jockey-gtk (or in case you are using KDE run jockey-kde) and install the nvidia drivers from there, then you should have no problems.

In general, as a beginner don't install programs that are not in the repositories, more than 95% of any packages you like you can get via your package manager.

---

### Post by jimmybarcelona on 2009-09-18
the only reason I tried all this crazy stuff is because it wouldn't work straight out of the repositories. I tried installing the most up to date driver from the hardware device manager and it caused an xserver crash. I had to go in and restore my xorg.conf file from the command line. I tried using envy, but it said that my system didn't support envy.
 I'm using ubuntu studio instead of plain ubuntu, so I know that it uses a different kernel to reduce latency. I don't even know what that means, but that was one of the tidbits of information I stumbled across while googling for solutions.
Does using ubuntu studio instead of ubuntu change which repositories I should be checking or how I should go about things?

---

### Post by hal10000 on 2009-09-19
[QUOTE]the only reason I tried all this crazy stuff is because it wouldn't work straight out of the repositories[QUOTE]
OK, then i guess you are on the right way to get your drivers running.hat points to one of these header-directories. You may post the output of the command
[COLOR="Red"]ls -ld /usr/src/*[/COLOR]

Look into your /usr/src directory and see if there's a symbolic link called "linux" (without quotes).
DOes this "linux" link (if it exists) point to your linux-rt-headers-2.6.28-3-rt directory? If so, then remove the link and let it point to the other directory:
```

sudo rm -rf /usr/src/linux && sudo ln -s /usr/src/linux-headers-2.6.28-3-rt /usr/src/linux

```
if it points to the other header-directory then do it this way:
```

sudo rm -rf /usr/src/linux && sudo ln -s /usr/src/linux-rt-headers-2.6.28-3-rt /usr/src/linux

```

If your "linux"-link doesn't exist, then create it. As i don't know which one of your header-directories is the right one, you probably have to test both of them:
```

sudo ln -s /usr/src/linux-rt-headers-2.6.28-3-rt /usr/src/linux

```
Then you can try to compile your drivers again.

I hope this can help you

---

