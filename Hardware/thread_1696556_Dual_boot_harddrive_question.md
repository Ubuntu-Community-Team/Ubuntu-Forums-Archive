---
title: "Dual boot harddrive question"
date: 2011-02-27
forum: Hardware
---

### Post by whiteknight2012 on 2011-02-27
Hello forum,
I am planning to buy an external hard drive, partition it, and install ubuntu on one partition. The other partition would be used for windows backup. 
However, i was wondering if i could somehow use the non ubuntu partition as a "dropbox" of sorts, so i could backup my files onto it and then access them through both operating systems. 
Would this work? Would i have to format the partition to fat32 or something? Is this possible at all?
Ant insight would be appreciated, Thanks!

---

### Post by YesWeCan on 2011-02-27
Ubuntu can read all formats but Windows cannot. :)
So you can format the spare area using Windows (normally as NTFS) and Ubuntu will be able to read and write that partition no problem.

Also, I recommend installing the Ubuntu bootloader, Grub, on the master boot record of the USB drive. Then you boot off the USB drive. Otherwise you will overwrite the Windows MBR on your internal drive and you won't be able to boot Windows when the USB drive is not connected.
You see, Grub is in two parts - one on the MBR and sectors immediately after it, and one on the Ubuntu partition. This is unintuitive and gets a lot of folk into trouble.

Expect Ubuntu to be a little sluggish running off USB.

---

### Post by whiteknight2012 on 2011-02-27
Just what i wanted to hear! Haha thanks

---

