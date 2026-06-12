---
title: "Partitionned USB"
date: 2008-11-09
forum: Hardware
---

### Post by zancoste on 2008-11-09
Hello all,

I am not really sure if the question Even belongs on Ubuntu forum, but maybe someone might be able to help.

So I partitioned my 8GB flash drive. All is fine. I am able to see both partitions when I plug in the USB drive while I am in Ubuntu.

However, when I plug in the USB on Windows, I am only able to see ONE partition (the first one but not the second) and the weird thing is, when I run a virtual machine wile being in Windows XP and I plug my partitioned hard drive, the Ubuntu running in the Virtual machine is being able to see BOTH partitions... So it looks like XP doesn't assign a letter to that second partition. 

is there anyone who can help me make XP assign a letter to that second partition?

And i am sure the question will rise and someone will ask: "Why partition a USB drive in teh first place?" Well, I have a Xunbuntu on the first partition of my 8 GB usb drive, I use it to boot other computers and/or messed up systems.


Thanks for you help.

Edit: 
I made sure that the second partition was FAT and readable by WinXP. While using Disk Management, it is possible to see the second USB partition. XP just refuses to assign it a drive letter. Turns out, Win XP won't do so for any Removable drives with partition (98 and 2000 would though).
So the only way you can make a partitioned USB drive readable under Windows XP -- **the only OS that doesn't allow that** is to flip the "RMB" (removable media Bit). There are utilities that can help you do that.

Peace and Thanks.

---

### Post by WaeV on 2008-11-09
Windows can't see ext2 partitions by default.

---

### Post by zancoste on 2008-11-09
I made sure the second Partition was FAT, not any file systems only Linux can recognize.

---

### Post by 14218f4114b1fd99 on 2012-01-18
I have a Integral USB Stick but Lexar BootIt does not work.

---

### Post by sudodus on 2012-01-18
Windows XP does not see (or as you state it does not assign a volume letter to) more than one partition on a USB drive. But when you make a USB boot drive you can leave the first partition to Windows and make the second one your boot partition. Look at my solution in the following link.

[[COLOR="Red"]_http://ubuntuforums.org/showpost.php?p=11546560&postcount=5_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=11546560&postcount=5")

There are even a U3-system device /dev/sr1 and a swap partition on the little USB stick, and that will not disturb the boot process.

*Edit: By the way, please write new posts instead of editing in your first one, that makes it easier for us to find out that you have been writing.*

---

### Post by coffeecat on 2012-01-18
@sudodus, thanks for the information, but I'll close this old thread that was necromanced by the poster before you.

@saleemrashid1, it is not clear from your post whether you are asking a question or making a statement. If you have a technical problem you need help with, please start your own support thread rather than trying to resuscitate an old one. Also - as far as I can see, Lexar BootIt is Windows software. If you are trying to get it to work, you may be better off asking your question on a Windows forum.

Thread closed.

---

