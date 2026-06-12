---
title: "lost partitions"
date: 2009-07-22
forum: Installation &amp; Upgrades
---

### Post by eng.reem on 2009-07-22
hello, i was running Gparted on Ubuntu 9.04 jaunty while  by mistake i created a new partition table and lost all my data !
when i rebooted i got error 22 at stage 1.5
i put the live CD and tried to restore data by these commands :

> sudo grub
find /boot/grub/stage1

but i get this error :
> Error 15: File not found

any help plz ? i need to restore my data !:(

---

### Post by az on 2009-07-22
> **eng.reem said:**
> hello, i was running Gparted on Ubuntu 9.04 jaunty while  by mistake i created a new partition table and lost all my data !
when i rebooted i got error 22 at stage 1.5
i put the live CD and tried to restore data by these commands :



but i get this error :


any help plz ? i need to restore my data !:(

Boot the live cd, install Testdisk and run testdisk on your hard drive.

Testdisk can scan you drive for partitions and then add them to the partition table.

Don't panic!  Wiping your partition table is no big deal if you have a live cd handy.  All your data is still there, it's just a question of putting the partition table back to what it was.

---

### Post by eng.reem on 2009-07-22
thanx for ur reply, actually now i downloaded Testdisk on the live cd but it doesn't work,when i click on it nothing happens !

---

### Post by az on 2009-07-22
> **eng.reem said:**
> thanx for ur reply, actually now i downloaded Testdisk on the live cd but it doesn't work,when i click on it nothing happens !

You run it from the command line:

Example:
sudo testdisk /dev/sda

You may need to enlarge your terminal dialogue box.  It will prompt you if his is the case.

---

### Post by eng.reem on 2009-07-22
> **az said:**
> You run it from the command line:

Example:
sudo testdisk /dev/sda

You may need to enlarge your terminal dialogue box.  It will prompt you if his is the case.

i get command not found

---

### Post by az on 2009-07-22
Did you install it?

sudo apt-get install tesdisk

sudo testdisk /dev/sda

---

### Post by eng.reem on 2009-07-23
ya i installed it ,now the problem of : command not found solved
as i had to enable Community-maintained Open Source software (universe) ,i used testdisk and written the partitions ,but now i get grub error 17 when booting ,how can this be solved ?

---

### Post by oldfred on 2009-07-23
In the changes you made your partitions got renumbered. You can reinstall grub as you mentioned in your first comment and or edit your menu.lst.
Additional info is here:
[http://members.iinet.net.au/~herman546/p15.html#17]("http://members.iinet.net.au/%7Eherman546/p15.html#17")

---

