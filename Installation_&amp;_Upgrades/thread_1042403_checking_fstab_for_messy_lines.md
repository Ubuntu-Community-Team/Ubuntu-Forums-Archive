---
title: "checking fstab for messy lines"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by KerryLB on 2009-01-17
Hi people

An application I've been using would tell me line 13 in fstab was messy every time I started the app up. I eventually got round to fixing the line. (changed it from:
/dev/sda5  /drives/a_fat vfat -o iocharset=utf8,umask=000
to:
/dev/sda5  /drives/a_fat vfat iocharset=utf8,umask=000 0 0

Now I'd like to check again if my fstab contains any errors. Unfortunately I've forgotten the application that was bringing up this 'messy fstab' message.

Is there some kind of terminal command or utility that checks fstab for messy lines? Otherwise, what applications check your fstab when you start them up?

Thanks!
Kerry

---

### Post by tommcd on 2009-01-17
> **KerryLB said:**
> 
Is there some kind of terminal command or utility that checks fstab for messy lines? Otherwise, what applications check your fstab when you start them up?


The kernel reads fstab and uses the info to mount partitions. Here is a good tutorial for understanding fstab:
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)
Fstab's columns consist of device, mount point, file system type, options, and dump and fsck options. As long as your drives and partitions mount ok your fstab works. The **-o** that was removed in your example is just a shorthand for options, which is unnecessary in fstab.

If you read "man mount" you can read up on all the various mount options for different file system types.

---

### Post by KerryLB on 2009-01-18
Thanks for the link tommcd. I'm actually just looking for some kind of tool or command that will take a look at my fstab file and tell me if there are any errors or unfound partitions in it.

But I did read that article, and I learnt some interesting new things about mounting partitions :)

---

