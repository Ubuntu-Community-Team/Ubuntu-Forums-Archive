---
title: "Partitioning"
date: 2009-01-23
forum: Installation &amp; Upgrades
---

### Post by daniel014 on 2009-01-23
I have a Compaq Presario laptop with a 40GB HDD.
I want to dual boot Win XP and Ubuntu (Win is already installed).

Which file system should I use for Ubuntu?
How would I restore the laptop to just Win XP on the HDD if I wanted to unistall Ubuntu later?

Thanks in advance. :)

---

### Post by Pumalite on 2009-01-23
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
You can erase the Ubuntu partition and restore your Windows MBR with the Installation CD or Super Grub.

---

### Post by daniel014 on 2009-02-14
Bump

---

### Post by DeMus on 2009-02-14
> **daniel014 said:**
> I have a Compaq Presario laptop with a 40GB HDD.
I want to dual boot Win XP and Ubuntu (Win is already installed).

Which file system should I use for Ubuntu?
How would I restore the laptop to just Win XP on the HDD if I wanted to unistall Ubuntu later?

Thanks in advance. :)

For Ubuntu I use the ext3 file-system for / (root) and /home and swap for the swap partition.
When you want to restore to only Windows XP you can simply erase the Ubuntu partitions in the discmanager in Windows XP, where you can also create a new Windows partition which you can use for data, or whatever.
To restore the MBR (as Pumalite also wrote) you can use your Windows install disk.
Restoring the MBR is not necessary, but when you don't do it you will always see your Ubuntu Grub boot menu when you start your computer. Restoring the MBR will give you XP directly.
Success.

---

