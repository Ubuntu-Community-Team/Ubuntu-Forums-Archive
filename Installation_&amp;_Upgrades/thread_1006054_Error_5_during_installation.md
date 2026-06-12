---
title: "Error 5 during installation"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by FRGIV92 on 2008-12-08
I was installing Ubuntu with an official CD and about 30% in it gave me an error message Error 5 it said it had problems copieing files and to clean the CD or CD drive reader, i know its not either the CD is spotless and my CD reader reads plenty of other CD's fine what do i need to do to resolve the issue?

---

### Post by FRGIV92 on 2008-12-09
I forgot to say that it also says its an Input/output error

---

### Post by Pumalite on 2008-12-09
Quoted from the GNU/GRUB manual

    5 : Partition table invalid or corrupt
        This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign. 

Check the partition table by running fdisk as root ('sudo fdisk -lu) in Linux, or use your favourite partition editing software to make sure one of your partitions has been marked 'active'.

GRUB's 'makeactive' command is used for setting a boot flag on a partition, so you can also do it with GRUB. Windows in particular requires a boot flag or it won't boot.

If more than one partition has already been marked as active, you might need to remove the 'active' flag from one of them, as only one is supposed to be set as active at a time. Use your favourite partition editing software for that.

If nothing else works, you might be able to use TestDisk to write you a brand new partition table.
TestDisk is an excellent Linux program that can scan you hard disk for partition starting blocks and identify those and offer you the chance to have the one you select written to a new partition table for you. TestDisk can do lots of other useful jobs as well. This website has its own page about TestDisk, TestDisk Page.

You should always back up your data before using any software to work on your partition table.
If you can't boot any operating system you might need to use a Live CD for doing that, and you can visit these links to learn how, File Systems and Mounting Page, SSH Network.

[http://users.bigpond.net.au/hermanzone/p15.htm#5_](http://users.bigpond.net.au/hermanzone/p15.htm#5_)

---

