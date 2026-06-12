---
title: "Partition dividing when installing Ubuntu"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by Adavur on 2009-06-13
Hi folks.

I'm going to install Ubuntu today on my PC. My computer came with three preinstalled partitions: C BOOT, where my Windows XP is placed, E RECOVERY, which I wont change anything ;), and D BACKUP where I currently have the Windows 7 RC installed, just to try it, I swear, I love Linux :D.
But anyway, C BOOT and E RECOVERY should stay as the are, where I want to install Ubuntu is on D BACKUP. My problem is that there is Win7 placed, and I would really like if it could stay there a couple of months more. I would proberbly uninstall it during the summer, but not yet.
Is there a way to "divide" partition D BACKUP into one with about 15 gb to Win7 and one with about 80 gb to Ubuntu without deleting Windows 7 RC? And if yes, can I then kinda "merge" them together after I've uninstalled Windows 7 again, and give the space to Ubuntu?

I know really nothing about this, but could any of you please help me with this. How should I do if I want to keep my to Windows and still have Ubuntu?

Greetings! :)

Mathias.

---

### Post by PureLoneWolf on 2009-06-13
I have Partition Magic, which certainly works for XP partitions, I am not entirely sure about Windows 7 partitions though, I don't know if they messed around with NTFS for Win7.

The GParted live CD seems to be able to work with NTFS for all operations.  Give that a try, but always backup...

[http://gparted.sourceforge.net/features.php](http://gparted.sourceforge.net/features.php) <-- Confirms NTFS

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) <-- download

Hope that helps

---

### Post by Adavur on 2009-06-13
Thank you, I will take a look at it :)

---

### Post by Adavur on 2009-06-13
Just one question: Am I able to divide a partition without deleting any files?

---

### Post by Partyboi2 on 2009-06-13
Yes you can resize partitions without having to delete files, but it its always recommended to backup your important stuff before working on partitions.

---

### Post by Adavur on 2009-06-13
Great, thx for the answer. :)

---

