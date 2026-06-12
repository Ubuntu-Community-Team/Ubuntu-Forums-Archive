---
title: "Temporarily add hard drive to system"
date: 2008-02-19
forum: Hardware &amp; Laptops
---

### Post by stevecoh1 on 2008-02-19
I have a new machine that's running Ubuntu 7.1.  I had an old machine that crashed albeit with a perfectly good hard drive that was running CentOS 5. This drive has lots of data that I'm interested in moving over.  So my plan would be to temporarily add this drive to the system, mount it, and copy the data.

I physically add the drive, reboot.  The BIOS boot loader can see the second drive but I don't want to boot from it, it's not bootable on this machine (Dell Inspiron 530 does not support CentOS or RedHat and kernel panics if I try, but then I've already given up on that) -  I just want to transfer the files, so I boot normally.

I can't even see the hard drive:

fdisk /dev/sdb doesn't find the device.

Using parted, I can see the device /dev/sdb, but I'm not familiar enough with parted to know what to do with it.  

What do I need to do to make the second drive visible to fdisk?

---

### Post by jan de beuker on 2008-02-19
to see if your drive is there use

sudo fdisk -l

When  the drive is there  try to mount it

---

### Post by stevecoh1 on 2008-02-19
You're right - THANKS!

That's weird.  I'd have thought fdisk /dev/sdb2 would have found it.

---

### Post by jan de beuker on 2008-02-20
fdisk /dev/sdb2 is the command to check the disk

---

### Post by stevecoh1 on 2008-02-20
OH, duh.

It's fdisk /dev/sdb I need to use.

---

### Post by jan de beuker on 2008-02-20
If you want to know how fdisk works type

man fdisk

---

