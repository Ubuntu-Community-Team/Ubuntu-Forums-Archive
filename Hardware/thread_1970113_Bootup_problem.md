---
title: "Bootup problem"
date: 2012-04-30
forum: Hardware
---

### Post by ?#Yhf%*&amp; on 2012-04-30
I accedentally switched off my Ubuntu netbook while it was loading something, and when I powered it back on it did this. I think the kernel got corrupted, and I'm posting this from an Ubuntu 11.10 Live USB (the netbook was running Ubuntu 12.04). Any help would be great!

---

### Post by ahallubuntu on 2012-04-30
From the live usb, try running e2fsck on your partition that had the root file system:

sudo e2fsck /dev/sda1

replacing /dev/sda1 with whatever the partition is in your case...

---

### Post by whiskers751 on 2012-05-01
Eesh... A kernel panic...!
Yes - run a fsck on your filesystem. That may shed some light.

---

### Post by ?#Yhf%*&amp; on 2012-05-01
I know, kernel panics suck. But I've gotten a ton on the Mac. Here's what fsck gave me:

```
e2fsck 1.42 (29-Nov-2011)
/dev/sda1: clean, 334808/15204352 files, 8800813/60789760 blocks

```

I also ran Disk Utility and it came out with nothing. I'm not sure what to do :/

---

### Post by ?#Yhf%*&amp; on 2012-05-01
Anyone? :(

---

### Post by whiskers751 on 2012-05-02
Chroot into your installation and install another kernel. Can you boot that?

---

