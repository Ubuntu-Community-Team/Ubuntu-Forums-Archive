---
title: "Uninstalling 9.10?"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by LarryXIII on 2009-11-04
I recently installed Ubuntu 9.10, but I decided to uninstall Ubuntu because it lags up my computer(too much file to load on a slow HDD). How do I uninstall it? Also, I didn't install through Wubi.

---

### Post by jjcv on 2009-11-04
You can simply remove the disk partition using a partition editor.  You could start up the Live CD and then run

sudo fdisk /dev/sd0   (replace sd0 with your hard disk).

The type "p" to list the hard disks

type "d" to remove a partition (you will need to give it the number of the partition to remove.

type "w" to save the partition table

That's it.  You not have an empty space on your disk to use as you please.

---

### Post by par.android on 2009-11-05
Or for a more graphical way in a LiveCD type 'sudo gparted' and format the partitions.

---

### Post by sliketymo on 2009-11-05
If you dual-booted with windows,you can delete the partition using the windows disk management app.You will probably have to fix your windows MBR,if you installed grub onto it.

---

### Post by MilosZ`90 on 2009-11-06
> **sliketymo said:**
> If you dual-booted with windows,you can delete the partition using the windows disk management app.You will probably have to fix your windows MBR,if you installed grub onto it.

That should fix my Ubuntu 9.10 problem... But I don`t know how to fix MBR... Any help with that? I`m not certain does it make any difference that I`v installed it using wubi... If it does can anyone help me with that?

---

