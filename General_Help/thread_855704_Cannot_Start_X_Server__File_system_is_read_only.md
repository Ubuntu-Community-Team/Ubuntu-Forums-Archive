---
title: "Cannot Start X Server / File system is read only"
date: 2008-07-10
forum: General Help
---

### Post by braindrive on 2008-07-10
Till today morning my laptop running Ubuntu 8.04 was working fine. I did a shutdown yesterday night and while trying to boot up this morning, the X Server was not able to start and the whole system had become read only.

I might have installed updates which came in within 2 days but I have not done something like editing /etc/fstab and mounting some drive etc.

Any help would be appreciated.

I am running Ubuntu 8.04 on an old Dell 600m XVGA 1400 x 1050 display, Pentium M processor, 1 Gb memory.

---

### Post by cmnorton on 2008-07-10
Boot into recovery mode, and start looking at the output of dmesg and the tail of
/var/log/messages
/var/log/syslog

This is an educated guess, but it sounds like your file system needs to be recovered. 

Look at fstab, ro is the state the file system goes into when something goes wrong. Here is part of my /etc/fstab

UUID=863a6427-d6f1-44cc-b1ff-5b18523db9a0 /               ext3    defaults,errors=remount-ro 0       1

I strongly suggest you research running fsck using a live cd, Knoppix, Ubuntu live CD, etc, if indeed this is the problem.

I also do not know the boot options you need to look at all messages in the display. It might be alt+f1. That might let you see more during the boot.

---

### Post by Fixman on 2008-07-10
> **braindrive said:**
> Till today morning my laptop running Ubuntu 8.04 was working fine. I did a shutdown yesterday night and while trying to boot up this morning, the X Server was not able to start and the whole system had become read only.

I might have installed updates which came in within 2 days but I have not done something like editing /etc/fstab and mounting some drive etc.

Any help would be appreciated.

I am running Ubuntu 8.04 on an old Dell 600m XVGA 1400 x 1050 display, Pentium M processor, 1 Gb memory.

```
 /boot/grub/menu.lst 
```

---

### Post by bodhi.zazen on 2008-07-10
If the whole system is ro, that implies a problem with the file system.

From the command line :

```
sudo shutdown -Fr now
```

---

### Post by braindrive on 2008-07-10
Thanks guys. I will try your suggestions and will let you know.

---

### Post by cmnorton on 2008-07-11
> **bodhi.zazen said:**
> If the whole system is ro, that implies a problem with the file system.

From the command line :

```
sudo shutdown -Fr now
```

I could not find -F in the man shutdown. Does this create forcefsck in the root directory?

---

### Post by bodhi.zazen on 2008-07-11
Yes, it is documented here :

[http://linux.die.net/man/8/shutdown](http://linux.die.net/man/8/shutdown)

> The **-F** flag means 'force fsck'. This only creates an advisory file */forcefsck* which can be tested by the system when it comes up again. The boot rc file can test if this file is present, and decide to run **fsck**(1) with a special 'force' flag so that even properly unmounted filesystems get checked. After that, the boot process should remove */forcefsck*.

---

