---
title: "upgrade wubi to full install AND ditch windows...?"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Sarai the Geek on 2009-02-18
I installed ubuntu using wubi a while back. I love it and very rarely log into windows anymore, and I have been thinking about getting rid of the windows completely and just using a virtual box for the few programs I need.

I got an excellent excuse to do so today, when my vista installation decided to become unbootable. I've managed to recover the few files I had left in the windows install, which are now all backed up on my external hard drive for safekeeping.

There are a fair amounts of guides out there for upgrading a wubi installation to a full install but usually they show you how to move it to a new separate partition. Since the vista doesn't work any more, I would like to just replace it altogether with ubuntu.

My hard drive has two partitions, sda1 and sda2. Sda 2 is a recovery drive that was built into the computer and sda1 is everything else. The recovery drive is obviously worthless (didn't help in the slightest recovering my vista install), so I can ditch that too.

I installed lvpm and it gives me the option to upgrade to the sda1 partition. Is that what I should do?

---

### Post by hansdown on 2009-02-18
Hi Sarai the Geek.

If you have an ubuntu install disk, boot from disk, select install, and when it comes to the partitioning screen, choose guided use entire disk.
It will install over your other system.

---

### Post by lvleph on 2009-02-18
There is a tool to migrate your wubi install to a partition. What you can do is shrink you vista partition and then use the shrink space as your new root and swap. Once you have everything migrated over you can then use the windows partition as you home partion. All you need to do is reformat it to ext3 and then look up how to move your home to a partition. The wubi migration tool is easy to find through google. Also, I posted a dual boot from iso a couple days ago that has a link to it.

---

### Post by Sarai the Geek on 2009-02-18
> **lvleph said:**
> There is a tool to migrate your wubi install to a partition. What you can do is shrink you vista partition and then use the shrink space as your new root and swap. Once you have everything migrated over you can then use the windows partition as you home partion. All you need to do is reformat it to ext3 and then look up how to move your home to a partition. The wubi migration tool is easy to find through google. Also, I posted a dual boot from iso a couple days ago that has a link to it.

Can I resize the partition from within ubuntu? I can't boot into windows, remember?

---

### Post by emerson1234567890 on 2012-01-27
you can use the disk utility in Ubuntu.
If you cant find it (which i do but I know it's hidden somewhere) boot from the [GParted]("http://gparted.sourceforge.net/") Live CD or LIVE USB Stick.

---

### Post by bcbc on 2012-01-27
You can't resize the disk that Wubi's virtual disk is mounted on. If you can't boot Windows, then you will have to use an alternate method to migrate:

[http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration](http://askubuntu.com/questions/93954/how-do-i-get-rid-of-windows-during-wubi-migration)

---

### Post by lisati on 2012-01-27
Back to sleep.....

---

