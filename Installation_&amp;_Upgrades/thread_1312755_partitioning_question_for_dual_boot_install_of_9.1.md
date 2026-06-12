---
title: "partitioning question for dual boot install of 9.10"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by gatorbrit on 2009-11-03
Hi, I am doing a fresh install of 9.10 on my Dell workstation.  I have winXP installed and the partitions are:
/dev/sda
/dev/sda1 fat16, 41MB
/dev/sda2 ntfs, 249958 MB

I want to put ubuntu on this drive, but there is no free space to create the partition.  BUT I know that I am only using about 30MB of sda2.   

Do I need to seperately create a partition before I start the install, or will ubuntu allow me to partition this drive now?

Thanks

---

### Post by bruno9779 on 2009-11-03
Ubuntu should allow you to resize the partition, but not always.

Play it safe, and partition your windows drive from windows itself with an app like [these]("http://www.tech-faq.com/Partition-Software.shtml")

then pop in the Ubuntu live CD, chose the manual option, and have it format the freed space as ext3 or ext4

---

### Post by gatorbrit on 2009-11-03
> **bruno9779 said:**
> Ubuntu should allow you to resize the partition, but not always.

Play it safe, and partition your windows drive from windows itself with an app like [these]("http://www.tech-faq.com/Partition-Software.shtml")

then pop in the Ubuntu live CD, chose the manual option, and have it format the freed space as ext3 or ext4


OK, I don't think that it is allowing me to change the partition.   SO I just need to do it myself and I just create a large enough ext3 (or 4) partition?  Do I need to create a swap partition as well?

My other problem, is that I have to recover my MBR so I can actually boot to windows.   uggh.

Thanks

---

### Post by bruno9779 on 2009-11-03
Maybe you should look at something like [this]("http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm")

It follows every single step, and you should replace ext3 with ext4 as it is the default since 9.10 (some may argue there, but no issues for me)

Still, if you resize from Win is better to leave the partiton unformatted and have ubuntu formatting it to ext*.

---

### Post by gatorbrit on 2009-11-03
I sort of solved it.   I hadn't used winXP for about a year, so I just installed ubuntu over the win partition!

---

### Post by bruno9779 on 2009-11-04
> **gatorbrit said:**
> I sort of solved it.   I hadn't used winXP for about a year, so I just installed ubuntu over the win partition!

:lolflag:

I think that you have found the best solution possible:
```

sudo apt-get purge Win-dose
```

---

### Post by gatorbrit on 2009-11-04
Yup, sometimes you just have to cut the chord and get on with your life.

9.10 is really nice though!

---

### Post by bruno9779 on 2009-11-04
I am not too happy about the login screen, but everything else is just grest.

I love the preloaded wallpapers selection!!!!! :KS:KS:KS:KS:KS (5 stars rating!!)

---

