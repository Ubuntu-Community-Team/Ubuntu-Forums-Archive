---
title: "Hdd"
date: 2010-03-25
forum: Hardware
---

### Post by Linux Lover II on 2010-03-25
Hello,

I bought a laptop with windows 7, but decided to perform a wubi-install of 9.04, and honestly, I enjoy it.

I even got Word 2007 and Photoshop CS 4 working, so :)

Only problem: due to wubi install, only 40 GB is dedicated to Ubuntu, which is far too less :o

How can I change this, without re-installing everything (I spent quite some time adapting it to my needs :p )?

Could anyone help me with this please?

Thanks in advance for this great forum!

---

### Post by gordintoronto on 2010-03-25
If you click Places/Computer, the rest of your hard drive should show up, perhaps as xxx.x GB Media. Ubuntu has complete access to all of it.

---

### Post by Linux Lover II on 2010-03-25
> **gordintoronto said:**
> If you click Places/Computer, the rest of your hard drive should show up, perhaps as xxx.x GB Media. Ubuntu has complete access to all of it.

Thanks for your reply!

What you say, is true, however, linux continues giving me alerts: 1.1 GB free, while the rest of my 500 GB HD remains free...
So this does not solve the problem, I guess... I included a screenshot, maybe that describes my problem more clearly.
By the way: where are new programs installed?

Greetz & thanks again!

---

### Post by adam814 on 2010-03-25
On a normal install with extra free space somewhere else you could just adjust partitions using gparted, but I cringe at the thought of trying that with a wubi install.

I'd suggest backing up everything first, making a proper partition for Ubuntu, then copying the backup over and re-installing GRUB.

Installed programs should just be in the menu, sometimes you do have to look for them a little.

---

### Post by Linux Lover II on 2010-03-25
> **adam814 said:**
> On a normal install with extra free space somewhere else you could just adjust partitions using gparted, but I cringe at the thought of trying that with a wubi install.

I'd suggest backing up everything first, making a proper partition for Ubuntu, then copying the backup over and re-installing GRUB.

Installed programs should just be in the menu, sometimes you do have to look for them a little.

Thank you for your reply!

But my preferences will stay unaffected? E.g. a virtual box : will I have to re-install it or not?

---

### Post by Linux Lover II on 2010-03-25
Another idea:

isn't it possible to install programs from ubuntu on the file system (which is +- 300 Gb)?

Or can't I create another partition where Linux can install additional software I want?

---

### Post by gordintoronto on 2010-03-25
Do you have Administration/Computer Janitor?  It might clean up enough to be significant.  The .deb files you have downloaded for system updates or installing software sit in your root until you clean them up.

Log files also just grow and grow.

---

### Post by adam814 on 2010-03-25
Actually you should be able to.  I don't know why I didn't think about that.

I'd still back it up before trying this:

Defragment your C: drive then shrink the volume from within Windows 7 (so it won't through a fit).  Then make a new ext4 (or whatever you prefer) partition in the free space using gparted in Ubuntu.

I'd suggest moving either /home or /usr to the new partition, depending on which will free more space for you.  I'd recommend /home as if you end up needing to reinstall you can keep your files and settings intact.

Copy "/home/*" to the new partition (it'll probably be mounted somewhere under /media).  Then add an entry for it in your /etc/fstab (There are tutorials on doing this, I recommend using the UUID instead of the entries under /dev).

This should work.  If it doesn't you still have your backup of course.

---

### Post by zsee on 2010-03-26
[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20resize%20the%20virtual%20disks?)
or
[http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)
Here, right under "how to get rid of windows"

It isn't a good solution unless you have a lot of free disk space...

---

### Post by Linux Lover II on 2010-03-27
Thanks to all for your replies!

I first tried to conver the wubi install into a full ubuntu dual boot, which failed
(grub error 22), nothing (even not windows) was able to boot.

So I recovered windows with the recovery cd.

Now I've tried to make another new virtual disk for the root, (150 gb), but after changing the names, it gives grub gnu 4.97 or something like that, with a minimal bashline: it says that the kernel is not loaded.

In the meantime, I'm running out of diskspace on this ubuntu version (about 100 mb remaining), so I'm in serious trouble...

Anyone who can help me?

Thanks in advance!

---

### Post by Linux Lover II on 2010-03-27
I tried to replace the wubildr, but that did not help neither.

---

### Post by Linux Lover II on 2010-03-27
> **Linux Lover II said:**
> I tried to replace the wubildr, but that did not help neither.


And at last: migrating wubi install gives unknown os in the startup screen.


I'm getting in serious trouble, ain't I?

---

### Post by Linux Lover II on 2010-03-27
> **Linux Lover II said:**
> And at last: migrating wubi install gives unknown os in the startup screen.


I'm getting in serious trouble, ain't I?

Update: now he says ubuntu on dev sda6

hower, when selecting this one, he jumps to unetbootin, which gives then error 15

Furthermore, there is an unknown os in the list, which gives error 12.



Anyone knows?

---

