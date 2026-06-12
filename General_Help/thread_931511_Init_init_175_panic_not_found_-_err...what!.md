---
title: "Init: /init: 175: panic: not found - err...what?!?"
date: 2008-09-27
forum: General Help
---

### Post by letmein on 2008-09-27
What the heck does this mean?

Init: /init: 175: panic: not found
Init: /init: 175: panic: not found
Init: /init: 175: panic: not found
Init: /init: 175: panic: not found etc...

I get this on ubuntu hardy boot up...how do i fix this?...correction, what steps do i need to take to fix this?

---

### Post by touchlikefire on 2008-10-22
I too, am getting this error.  For me, it happened when I updated the kernel and, unbeknownst to me I had run out of room on / (a bug, in my opinion, but that's for another post).  So the kernel update couldn't complete--specifically, I think it failed at updated the **initrd** and **vmlinuz** files...or something.

I booted up the live CD, and everything is appears in **/boot **correctly.  I played around with **menu.lst**, changing UUID's to /dev/sda(x) and removing options (eg - "selinux=1"), but still no dice.

I should mention right here that what predicated this incident was that I removed **selinux** from my system, which forced a recompilation (or whatever) of the kernel images, whereupon I ran out of hdd room and it failed.

So...now what?  Last night I tried to do an 'update-initrd' but I don't know the correct syntax.

As always, help is appreciated.

---

### Post by geirha on 2008-10-22
Are you able to boot the previous kernel?

If so, do so, make sure to make some room on / and /boot, then try ```
sudo dpkg --configure -a
``` to configure all packages that didn't get properly configured. If that doesn't help, try reinstalling the kernel package ```
sudo aptitude reinstall linux-image-2.6.24-21-386
```

---

### Post by touchlikefire on 2008-11-04
Thanks Gierha, I'm sure this info will help someone in the future. Since Intrepid was nearing release anyway, I went ahead and formatted my root & boot partitions.  I'll certainly come back to this post for the syntax if I need to reconfigure things!

---

### Post by mmasic on 2009-01-09
> **letmein said:**
> What the heck does this mean?

Init: /init: 175: panic: not found
Init: /init: 175: panic: not found
Init: /init: 175: panic: not found
Init: /init: 175: panic: not found etc...

I get this on ubuntu hardy boot up...how do i fix this?...correction, what steps do i need to take to fix this?

It happened to me last night.
Boot from alternate cd to access /dev/xxx
Make some room :)
cd /usr/sbin
update-initramfs -k all -d
update-initramfs -k all -c

This solved my "panic" problems.

---

