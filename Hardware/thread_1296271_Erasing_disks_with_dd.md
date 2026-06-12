---
title: "Erasing disks with dd"
date: 2009-10-20
forum: Hardware
---

### Post by Boris-- on 2009-10-20
Hello,

I'd just like to know how to do this and how long does it take. The reason is not being able to install any windows after formatting my win7 drive. Ubuntu works fine but I need XP for work. 

Thank you for your time!

---

### Post by az on 2009-10-20
> **Boris-- said:**
> Hello,

I'd just like to know how to do this and how long does it take. The reason is not being able to install any windows after formatting my win7 drive. Ubuntu works fine but I need XP for work. 

Thank you for your time!

Have you tried simply clearing the partition table and then trying to install Windows XP?

Use the partition editor, or parted from the command line, or cfdisk from the command line....

If that doesn't work, then repartition the drive and just dd the first few blocks of the new partition to which you want to install XP

sudo dd if=/dev/zero of=/dev/sda1 bs=512 count=10  ##Use correct device - may be different than sda1!!

That should remove any sign of the previous filesystem to the XP installer.

---

### Post by Boris-- on 2009-10-20
I have tried clearing the partition table, but it didn't help. I will try your solution now and report back.

Oh, and thanks for help!

---

### Post by az on 2009-10-20
> **Boris-- said:**
> I have tried clearing the partition table, but it didn't help.

Exactly what is the problem?

---

### Post by stinger30au on 2009-10-20
dban all the way

[http://www.dban.org/](http://www.dban.org/)

live bootable cd to totally destroy all data on hdd

---

