---
title: "What to do with multiple hard drives during install"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by jalvsmith on 2009-02-21
I am installing Ubuntu 8.10 on a desktop with 2 hard drives. One is a 13GB and the other is 75GB. The 13GB is installed as the master and the 75GB is installed as the slave. 

I'm not worried about saving any information on either as I am looking to use this machine as a learning platform. I am installing Ubuntu with the expectation of installing edubuntu on top of it.

What is the best idea of how to set up these hard drives now that I'm at the partition part of the install?

Joey Smith

450 Mhz PIII, 375 MB RAM, 13 GB master HD, 75 GB slave HD.

---

### Post by x33a on 2009-02-21
since the smaller drive is a bit too small, you can partition the larger drive like this:

1. 15 gb ext3(root)
2. 1gb swap
3. rest /home ext3, or as ntfs.

keep the 13 gb drive as slave.

---

### Post by jalvsmith on 2009-02-21
> **x33a said:**
> since the smaller drive is a bit too small, you can partition the larger drive like this:

1. 15 gb ext3(root)
2. 1gb swap
3. rest /home ext3, or as ntfs.

keep the 13 gb drive as slave.

Do I need to swap the drives in the computer to reflect the change as master/slave relationship?

What should I format the 13GB hard drive as, ext3?

Will this just allow me to mount the 13GB hard drive as extra storage as needed (such as a removable flash drive)?

Also, do I need to select a mount point for the 13GB hard drive?

Thanks for the help. I'm new, but I am trying to learn (and retain) as much as I can.

---

### Post by x33a on 2009-02-21
i don't know much about ide drives(i assume you have those). but i think, you should change the jumper settings.

format the other drive as ext3, if you don't intend to access it with windows(dual-boot).

i don't think you need to specify a mount point for the secondary drive. it will be automatically mounted.

---

### Post by jalvsmith on 2009-02-21
Thanks, I'll try your suggestions.

---

### Post by lha on 2009-02-22
In case you haven't installed yet, I'll tell you my view: Partition the smaller drive with two partitions, root 12.5 GB and swap 0.5 GB. (In fact, you could use a swap file instead of a partition, but it would require an extra step during installation.) I'd use the larger drive as /home. Given your situation, I favor this partition scheme because it gives you a simple setup with a dedicated home partition. In contrast, Jalvsmith's suggestion would leave you with an odd 13GB partition hanging around. (My root is ~7GB, so 12.5GB is definitely enough.)

Ext3 is the default, and its a safe choice. Since your computer is a bit low end, I recommend you to install the package xubuntu-desktop. It'll give you XFCE, which is lighter than Gnome, the default desktop environment in Ubuntu. There are also many other window managers you might eventually want to try.

---

