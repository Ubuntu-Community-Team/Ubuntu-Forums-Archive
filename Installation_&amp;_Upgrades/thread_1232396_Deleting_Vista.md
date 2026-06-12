---
title: "Deleting Vista"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by dino1515 on 2009-08-05
OK the time has come to get rid of Vista, I finally have Ubuntu running perfectly with XP in Virtualbox so I can sync my iPhone. I now want to get rid of Vista completely and add the space to Ubuntu, the only problem is I do not know how to do this.

I believe that I can either use gParted under System>Admin>Partition Editor to format the Vista Partition to ext3

or

I can use the Ubuntu disc to completely install Ubuntu again (on the whole system not dual boot) and reinstall all my programs etc... however this would take a long time.

What is the best way to do what I want to do?

One thing I am worried about is whether or not deleting the Vista Partition completely will delete all my drivers? Is that how it works? Will this ruin my whole computer or even just stop VirtualBox from running XP? Have I overlooked anything?

Any help is greatly appreciated!

---

### Post by hibliss on 2009-08-05
Good information here - [http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")

The first step will be to format the Vista partition, explained in the guide.

After you remove it, you will also want to remove it from the Grub menu, which is the easiest part.

---

### Post by Mark Phelps on 2009-08-05
> **dino1515 said:**
> OK the time has come to get rid of Vista, I finally have Ubuntu running perfectly with XP in Virtualbox so I can sync my iPhone. I now want to get rid of Vista completely and add the space to Ubuntu, the only problem is I do not know how to do this.

I believe that I can either use gParted under System>Admin>Partition Editor to format the Vista Partition to ext3
Just make sure that the Vista partition is not mounted.  If you've added that to your FSTAB, it WILL be mounted.  GParted can only work on unmounted partitions.

> I can use the Ubuntu disc to completely install Ubuntu again (on the whole system not dual boot) and reinstall all my programs etc... however this would take a long time.
Presuming you already have Ubuntu installed in its own partition(s), there is no need to do this.

> One thing I am worried about is whether or not deleting the Vista Partition completely will delete all my drivers? Is that how it works? 
It won't affect any of your Linux drivers,and no that is not how it works.

> Will this ruin my whole computer or even just stop VirtualBox from running XP?
Since you're running XP from inside Virtualbox in Ubuntu, removing Vista should have no effect at all.

---

### Post by presence1960 on 2009-08-05
Don't reinstall Ubuntu when it is working fine. just delete the vista partition using gparted either from the ubuntu live cd or gparted live cd. Then you have some options. You can create a new linux partition(s) for data or merge the unallocated space to your ubuntu partition. When complete reboot and edit menu.lst by removing your windows entry.

---

