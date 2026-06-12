---
title: "Problems dual booting with w7"
date: 2009-10-26
forum: Installation &amp; Upgrades
---

### Post by Kolkritan on 2009-10-26
I want to dual boot ubunty with w7. First I tried to install w7 first and then ubuntu, but for some reason my w7 didn't appreciate this much. So i decided to do it the other way around, and found [this guide](http://ubuntuforums.org/showthread.php?t=1035999) to help me. So I got myself this line at the end of my menu.lst:

title Windows 7 (Loader) 
 root  (hd0,1)
savedefault
makeactive
 chainloader+1

And tried tried N=0 to N=4 in root (hd0,N), all I got was Error 12: Invalid device request. My google skills told me to maybe try with rootnoverify instead, wich didn't help me anything, again with different values at N.

Any ideas?

Thx.

---

### Post by oldfred on 2009-10-26
Is the windows partition a primary partition? Windows has to be in a primary.

[http://members.iinet.net.au/~herman546/p15.html#12_](http://members.iinet.net.au/~herman546/p15.html#12_)

run this command so we can see your drive/partitions (with small L):
```

sudo fdisk -l  
```

---

### Post by Kolkritan on 2009-10-26
> **oldfred said:**
> Is the windows partition a primary partition? Windows has to be in a primary.

[http://members.iinet.net.au/~herman546/p15.html#12_]("http://members.iinet.net.au/%7Eherman546/p15.html#12_")

run this command so we can see your drive/partitions (with small L):
```

sudo fdisk -l  
```

```

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         365     2931831    5  Extended
/dev/sda2   *         366        1216     6835657+  83  Linux
/dev/sda3            1217        6082    39086145   83  Linux
/dev/sda4            6083        9730    29295616    7  HPFS/NTFS
/dev/sda5               1         365     2931799+  82  Linux swap / Solaris

```

---

### Post by oldfred on 2009-10-26
The boot * should be on the windows partition. Linux does not use it and  windows does. Theoretically the makeactive should say it is the boot partition when you select windows but I have heard of issues with vista where that actually caused problems.

Use the partition editor gparted on the liveCD to turn the boot flag on for the windows partition.

Also remove the makeactive line from the windows boot stanza in menu.lst.

Make this your entry:
title        Windows 7 (loader) on sda4
rootnoverify    (hd0,3)
savedefault
chainloader    +1

---

### Post by Kolkritan on 2009-10-27
:cry:> **oldfred said:**
> The boot * should be on the windows partition. Linux does not use it and windows does. Theoretically the makeactive should say it is the boot partition when you select windows but I have heard of issues with vista where that actually caused problems.
[...]

 
My windows partition now works properly (I'm currently browsing from IE :cry:). Though now when I start the ubuntu partition it sais there's already an X-server running at display 0. I then get an error message like this:
 
```
 
Ubuntu is running in low-graphics mode
[...]
(EE) GARTInit: Unable to open /dev/agpgart (No such file or directory)
(EE) [drm] drmOpen failed
(EE) intel(0): [dri]DRIScreenInit failed. Disabling DRI.
(EE) intel(0): Failed to allocate framebuffer. Is your VideoRAM set too low?
(EE) intel(0): Couldn't allocate video memory.

```Also, the touchpad or trackball won't load properly (though a USB mouse works as it should). I cannot log in to ubuntu at all, since everything seems to freeze when I have entered my UN and PW.

Edit: I solved the problem by simply re-installing ubuntu. This time w7 had no problems accepting grub.

---

