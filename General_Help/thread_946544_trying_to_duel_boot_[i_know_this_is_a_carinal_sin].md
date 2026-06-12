---
title: "trying to duel boot [i know this is a carinal sin]"
date: 2008-10-13
forum: General Help
---

### Post by Monotoko on 2008-10-13
Hiya guys, i know its really, really bad asking how to duel-boot with XP on a linux forum, but i dont know many places with the community being so knowledgeable about computers.

So, i have:
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7ab852fc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29652   238179658+  83  Linux
/dev/sda2           29653       30401     6016342+   5  Extended
/dev/sda5           29653       30401     6016311   82  Linux swap / Solaris

As you can see, i accidently installed Ubuntu on the entire hard-disk, deleting my XP partition, not a bad thing, perhaps, but i wanted to duel boot as Windows plays my games, and prints through the printer (after numerous failed attempts with WINE and numerous emulators, i find that i shall just have to install XP again)

So can i ask, how do i lower the size of sda1, get some empty space, and install XP on that? (i take it its going to need formatting in some way...NTFS i think it was, can you tell me how to do that?)

Thanks in advance, and again, i appologise for the cardinal sin :P

---

### Post by Het Irv on 2008-10-13
To me at lease dual-booting is not a cardinal sin, it takes a while to adjust to Linux, and Windows is really better at gaming, even if nothing else.

To resize your partitions you can use the Partition Editor on the Live CD, its located under System -> Administration.  There you should be able to resize your Ubuntu Partition and install Xp on the freed space.

NOTE: once you install XP it will overwrite GRUB and you won't be able to boot to Ubuntu.  To restore GRUB use this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Monotoko on 2008-10-13
Right, i did what you said, and it just says "Unknown Disk" on my XP installation, i then tried to make a partition using NTFS, it still says unknown disk, what do i do??

---

### Post by Het Irv on 2008-10-13
Your leaving it as empty space and not formating it right?  Once you finsh editing partitions you should see 1 "Unknown Disk" (Ubuntu) and some Free space.

---

