---
title: "How to uninstall ubuntu 8.04 and reinstall Windows XP?"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by Sanjay41 on 2009-11-11
Hi, I recently had a hard disc crash and decided to try Linux as I heard lots of good stuff about it. However I have been unable to connect to the internet as it does not recognise wireless networks. I spent a day trying to solve the problem but nothing worked. I then plugged an ethernet cable but firefox kept asing me for username and password and I dont even know of what. So I decided that maybe Ubuntu wasnt the right choice for me right now. I have heaps of work to do. So I ordered a recovery disc with Windows on it and decided to install it. However, my laptop refuses to boot from the CD even after entering the BIOS menu and changing boot order to start booting with the CD drive with the Windows cd in it...or even after I tell my computer to boot from the CD, my laptop still goes ahead and boots normally into Linux. Please help as I have totally run out of ideas. I would love to just be able to remove Ubuntu from my computer for now.

---

### Post by pullmoll on 2009-11-11
To get rid of ubuntu it should suffice to zap the MBR (master boot record). To do this you can open up a terminal and
```
sudo dd if=/dev/zero of=/dev/sda bs=1b count=1
```. Be warned that afterwards you will **not be able to boot from the HDD anymore** until you have installed a new MBR from (for example) a Windows setup CD.

---

### Post by benmoran on 2009-11-11
I'd hold off on doing that just yet. If your computer won't boot from the CD, Ubuntu has nothing to do with it. You need to figure that out first. Probably the CD you got is not bootable. Try booting from another CD, maybe the one you used to install Ubuntu with. Or better yet, try getting some help with your problems. I think you'll love Linux once you get everything figured out.

---

### Post by Mark Phelps on 2009-11-11
This might not help, but I have an older laptop that refuses to boot from, or read, CDs or DVDs once it warms up.  Appears to be an alignment problem with the laser lense because the laptop gets very hot very quickly.

So, if your laptop gets hot also, you could try booting from CD when it's cold, that is, when you first turn it on.

---

### Post by sawick61 on 2009-11-11
> **benmoran said:**
> I'd hold off on doing that just yet. If your computer won't boot from the CD, Ubuntu has nothing to do with it. You need to figure that out first. Probably the CD you got is not bootable. Try booting from another CD, maybe the one you used to install Ubuntu with. Or better yet, try getting some help with your problems. I think you'll love Linux once you get everything figured out.

.

---

