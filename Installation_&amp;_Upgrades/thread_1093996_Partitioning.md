---
title: "Partitioning"
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by pixiesnoot on 2009-03-12
Hi everyone,
I'm trying to install Ubuntu via wubi-installer.org, and it's asking me how I want to partition my hard drive. I also have windows XP on it. I'm doing it maually so that I can give it half and half, as opposed to the other options where it was all or nothing. On the list, I have a /dev/sda1 device, and I'm assuming that's windows, it takes up all but 8 MB. When I click on edit partition, it doesn't give me any options to decrease it's size, and 8 MB doesn't seem like enough for ubuntu. How do I do this?
Thanks, Pixiesnoot

---

### Post by surml on 2009-03-12
you could for example use any live-cd that comes with qtparted or gparted (havent tried gparted) to resize your partition

important: its not without risk, so backup your data!

...and defrag your partition under xp before starting!

---

### Post by avtolle on 2009-03-12
If using Wubi, Ubuntu is installed on a virtual drive within the Windows partition. The only partitioning question I recall from doing a Wubi installation was how big the drive should be. Defragging the drive is a very good idea, regardless of whether using Wubi or doing a traditional installation.

---

### Post by WatchingThePain on 2009-03-12
Hi,
The wubi normally goes in your free space if you have any (if not then you most likely will be able to make some).
Obviously you need to give it a reasonable amount.
When I used the wubi 40G is not bad but depends what you use it for.

---

