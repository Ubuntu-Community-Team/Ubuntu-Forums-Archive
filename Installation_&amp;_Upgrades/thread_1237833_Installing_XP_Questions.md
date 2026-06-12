---
title: "Installing XP Questions"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by shahgols on 2009-08-11
Hi everyone,

I am running 9.04 on my PC.  I've dedicated the whole HD to Ubuntu, but I need to open up a little (20GB max) for XP.  Currently I have 3 partitions on this HD as follows:

1.  15GB for /
2.  230GB for /home
3.  5GB for swap

I want to shink the /home partition by 20GB and install XP.  How would I go about doing that?  And also, after I install XP, I need to reinstall/fix the GRUB boot loader...how would I do that?  Any help will be appreciated.  Thanks!

---

### Post by RedSingularity on 2009-08-11
Did you look at gparted?  Type that in terminal to start the partitioner.  Very easy to use.

---

### Post by shahgols on 2009-08-11
Thanks for the hint, I'll take a look.   Is it going to move any data that is "in the way" so that I can have my /home partition intact?

---

### Post by shahgols on 2009-08-11
Just found this article by googling "gparted resize ext3 partition".  

[http://www.howtoforge.com/linux_resizing_ext3_partitions]("http://www.howtoforge.com/linux_resizing_ext3_partitions")

Seems like that's what I needed.  Thanks for your help.

---

### Post by RedSingularity on 2009-08-11
No problem:)

---

### Post by p2bc on 2009-08-11
Might seem obvious for some, but make sure you run GParted as Sudo.

With that said, you should really run GParted from the liveCD to insure that the files don't get corrupted while moving things around. Scenario: (Far fetch but to illustrate a point) GParted, a software installed and running on a drive, located say on sector 100-150 on the disk. While resizing said disk section 145-200 are moved, Gparted lags and freezes and basically in an endless loop. I only mention it,because it happened to me. Not sure what happened, half way throught the resizing my system just frozed up, and it was a complete lost. FYI :)

Now, better still, no PC bashing here, because I do use Windows from time to time for work, but there is the glorious thing called virtual machine. Basically, you can create a virtual hard drive, and using the same procedure as you would do any ways, install Windows on it. VirtualBox from Sun is pretty good, and free, and is even in Ubuntu repository. There are others with more features, but if all you need it to run Windows from time to time it is worth looking into, and you don't have to resize or partition you drive. And if you are interested it works with other Operating System as well. I have Ubuntu Server on one, Mint on another, Fedora. It is a great solution to try different distros, or installing new feature and trying them out before committing to them on you main system.

Enjoy

---

### Post by raymondh on 2009-08-11
+1 on virtualize XP.  That is, unless you require to dual-boot.

---

### Post by RedSingularity on 2009-08-11
> **raymondhenson said:**
> +1 on virtualize XP.  That is, unless you require to dual-boot.


I fully agree virtualization is the best way to go.  I like to keep my whole system linux based as much as possible.  If you are using heavy graphics though then dual boot is best.

---

### Post by shahgols on 2009-08-11
Thanks all, I've been running XP in virtualbox, but I have run into a situation where I have to dual boot.  Sucks, and I tried everything to avoid it, but no can do.

---

