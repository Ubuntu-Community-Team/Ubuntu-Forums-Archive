---
title: "Make a partiton having Windows XP alredy installed"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by carlosgs91 on 2009-07-20
.

---

### Post by Azyl on 2009-07-20
You can use the installer > guided resize (using the slider to allocate sizes in partitions from ubuntu), you can use partition magic or any other program that lets you play with partions and resise them so basically you cut from the 30 g partition 5 gb from you free space and creates a new one wich you can use to install ubuntu be carefull and back-up the criticall things on your computer in case the program you use does something wrong. srr for the english

---

### Post by carlosgs91 on 2009-07-20
.

---

### Post by prshah on 2009-07-20
> **carlosgs91 said:**
> I'd like to make a partition of 5GB to install Ubuntu 9.04 and leave the 25GB with Windows XP (without format Windows XP)

Very easily possible. Boot off the live CD, then go to System-Administration-Partition Editor, and "shrink" your Windows partition to 25Gb. Note that it is a good idea to take a backup, chkdsk and defrag your Windows partition from within Windows first.

If you are going to be using Ubuntu on a trial basis only, I'd suggest you to use the Wubi ("within Windows") installation. With this, you don't need to bother about partitioning worries; just boot into Windows, insert the Ubuntu CD and follow instructions by clicking the "Install within Windows" button. You can always convert your wubi install to a fullblown Ubuntu installation at your convenience later.

---

