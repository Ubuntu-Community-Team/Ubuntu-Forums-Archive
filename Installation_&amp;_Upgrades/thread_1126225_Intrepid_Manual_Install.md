---
title: "Intrepid: Manual Install?"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by Tsarevich on 2009-04-15
I have always partitioned the hard drive manually but when i was installing Intrepid (either server or desktop), the manual partition gives no partition table. What should I do?

---

### Post by tamas305 on 2009-04-15
I believe I had a similar problem, try this.

1) Go though the installer to the partitioner

2) Once there select manual install

3) Select the partition you want to install to and install it as the root drive (the / option)

4) Finish the install and hopefully it will work

-tamas

---

### Post by Tsarevich on 2009-04-16
I have actually used the method since years. But which partition you are talking about? That's what I am saying. Unusually, there is no partition listed under /dev/sda and I have to create a new table.

---

### Post by Tsarevich on 2009-04-16
Have a look in the picture now. The last time I tried it, not even the choice (whether manual or guided) was displayed and it jumped straight to the step you see here. Even pushing Back gives no output. Even unmounting the partitions and starting the installation again makes no difference.

---

### Post by tarun.winlin on 2009-04-16
Bump!!

This thread provided me information that I was looking for.

---

### Post by Tsarevich on 2009-04-17
> **tarun.winlin said:**
> Bump!!

This thread provided me information that I was looking for.

What the **** have you understood? My question is never answered. Even shittier is the fact that I can not even see those partitions i early Ubuntu installers while they are perfectly visible in fdisk.

---

### Post by tamas305 on 2009-04-17
That is very interesting. Hmmm... What does fdisk say?

Try [gParted Live]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") (download iso, burn it to a disk and boot) and see if it shows any partitions...and where did you install Ubuntu?

---

### Post by Tsarevich on 2009-04-18
> **tamas305 said:**
> That is very interesting. Hmmm... What does fdisk say?

Try [gParted Live]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") (download iso, burn it to a disk and boot) and see if it shows any partitions...and where did you install Ubuntu?

There is no question of gParted when the partitions are visible in Ubuntu itself. They mount properly in Nautilus, I am able to see the files in them. I even deleted a partition in fdisk and it went fine. I am using the Windows OS on one of the same partitions and all others function well. Even the hard disk is now visible (there is a /dev/sda entry in the table shown in the pic I posted.) I am able to create new partitions and my HDD measures 40020 MB (well and good). But Ihave not went further because I want my old p[artitions, not new ones to overwrite everything.

---

