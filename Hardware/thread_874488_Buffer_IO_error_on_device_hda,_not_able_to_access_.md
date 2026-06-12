---
title: "Buffer I/O error on device hda, not able to access SATA disk"
date: 2008-07-30
forum: Hardware
---

### Post by zyxnull on 2008-07-30
Hello all, I'm sorry I didn't post this answer on the right forum, but my current status forbid me to do so, however, i felt many would benefit from it, so here it goes.

I've just helped a friend which was having troubles installing Ubuntu 8.04 on he's Toshiba laptop. dmesg was filled with this messages:

Buffer I/O error on device hda

We tried the irqpoll tricks and other, none of them worked. All attempts to modify or list partitions on the hard disk simply failed, "fdisk -l" returned nothing at all, there were many other errors on dmesg.

To actually solve the problem you have to access the BIOS and clear the option "set hdd user password", that is, remove the password, once done you'll be able to see or change the partitions on the harddisk.

This is interesting, since Windows XP or Vista install just fine with this option active

Hope this helps someone

P.S.: Please forgive my bad english

---

