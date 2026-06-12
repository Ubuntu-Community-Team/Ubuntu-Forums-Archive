---
title: "[SOLVED] Resizing a partition"
date: 2008-03-16
forum: Hardware &amp; Laptops
---

### Post by zetjee on 2008-03-16
Hi all of you..

I need to make a partition on a hard drive but i want to resize the partition of which the system is booted. 

Somehow this doesn't work! Tried it with the liveCD but that didn't work either. Message I get when resizing tells me that there has been a failure during resizing the partition.

Anyone knows how to solve this?

Thanks in advance

---

### Post by zetjee on 2008-03-16
Do you need aditional information?

---

### Post by robertchahine on 2008-03-16
install the "geparted" from the add/remove list .
then try with it resizing;)

---

### Post by zetjee on 2008-03-16
Thats what i did, but still it didn't work. Its also the program that gave me the error message.

---

### Post by Ace2016 on 2008-03-16
> **zetjee said:**
> Hi all of you..

I need to make a partition on a hard drive but i want to resize the partition of which the system is booted. 

Somehow this doesn't work! Tried it with the liveCD but that didn't work either. Message I get when resizing tells me that there has been a failure during resizing the partition.

Anyone knows how to solve this?

Thanks in advance

Try using the [GParted LiveCD]("http://gparted-livecd.tuxfamily.org/") i used it to move my file systems around last week, it was great.

---

### Post by zetjee on 2008-03-17
Ill give it a shot. By the way, friends told me you cant resize a ext3 filesystem.. how about this? 

And is it possible with the LiveCD?

Thanks in advance

---

### Post by Ace2016 on 2008-03-17
> **zetjee said:**
> Ill give it a shot. By the way, friends told me you cant resize a ext3 filesystem.. how about this? 

And is it possible with the LiveCD?

Thanks in advance

i think there has been a misunderstanding, ext3 can be resized, its XFS that cannot be resized, refer to the table for a full feature list of what gparted can do with the filesystems:

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php)

---

