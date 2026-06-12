---
title: "Unable to access virtual terminals 1-6"
date: 2006-09-25
forum: Hardware &amp; Laptops
---

### Post by jsvidyad on 2006-09-25
Hi!!

  I have a dell inspiron E1505 with a core 2 duo processor and Nvidia GeForce Go7300 video card. When I try to access the console based virtual terminals(1-6), I just get a blank screen. i also have SUSE on the same machine and I do not have any problem there.

  Any help would be appreciated.

---

### Post by BitTorrentBuddha on 2006-09-25
Is it completely blank or is there a flashing white cursor? If the latter is true you don't have tty1-6 enabled. If that is the case, enable them by adding (or possibly uncommenting) these lines in /etc/inittab: ```
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6
```

---

### Post by jsvidyad on 2006-09-26
Those lines are there and they are uncommented, but still, I just get a completely blank screen.

---

### Post by BitTorrentBuddha on 2006-09-26
Hmm, I don't know what to tell you, perhaps it is a problem with your monitor or graphics card. If those lines are there, there should be VTs... Sorry :(

---

### Post by prana on 2006-09-27
Are you using the nvidia driver or the nv driver? With the nv driver you should have no problems but it can happen with the nvidia driver. You will have to add a vga=normal to your grub boot line to make the VTs work.

---

### Post by jsvidyad on 2006-09-28
I am using the nvidia driver. can you tell me exactly what I have to add and where??

---

### Post by eylisian on 2006-09-28
I was wondering that myself and did some digging.

[http://www.ubuntuforums.org/showthread.php?p=1541970](http://www.ubuntuforums.org/showthread.php?p=1541970)

Great howto.

---

### Post by jsvidyad on 2006-09-29
Thanks. It finally works.

---

### Post by cully on 2006-10-08
> **eylisian said:**
> I was wondering that myself and did some digging.

[http://www.ubuntuforums.org/showthread.php?p=1541970](http://www.ubuntuforums.org/showthread.php?p=1541970)

Great howto.

I had the same problem and this worked for me as well.  I used vga=791 instead of vga=normal, but I got my consoles back.  Also, I was having a problem where, halfway through the boot sequence, the text got all garbled.  This problem is now solved as well.  Plus, I get a cool 1024x768 console.

---

