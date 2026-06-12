---
title: "4TB E-SATA Disk doesn't automount after upgrade"
date: 2021-12-11
forum: Hardware
---

### Post by lagu26532 on 2021-12-11
I recently upgraded from Lubuntu 16.04 LTS to Lubuntu 20.04 LTS. My 4TB E-Sata disk which I've been using in Lubuntu 16.04 doesn't auto-mount anymore and is not listed by $fdisk -l. [COLOR=#000000]My PC is a HP Elitebook 8470p. I think the filesystem of my 4TB drive is ext4. How can I get my drive to mount?[/COLOR]

---

### Post by sudodus on 2021-12-11
How did you mount it before? Via "automount" or via an entry in /etc/fstab?

Have you checked if the file system is healthy?

Do you want it to mount automatically, when connected while the computer is running or mount automatically at boot?

---

### Post by lagu26532 on 2021-12-11
Via automount. The disk spun up and after that I could access it in Nemo, Nautilus, etc. Now the disk spins up but fdisk and lsblk doesn't list it.
You were right. The filesystem was not clean, but I put my old drive with Lubuntu 16.04 LTS in and repaired it. Now I have my new drive in (which I boot from). My 4TB esata drive is still the same (now repaired). But it still doesn't show up using the commands fdisk or lsblk.

---

### Post by sudodus on 2021-12-11
If fdisk and lsblk doesn't see the drive, something is very wrong. I can guess that either the file system is damaged, or the drive itself is damaged. Please Check the S.M.A.R.T. information and then check/repair the ext4 file system.

See the instructions at [this link](https://askubuntu.com/questions/972978/fsck-reports-that-filesystem-still-has-errors/972983#972983).

It is also possible that the eSATA connection or the external box is damaged or the power supply is not quite sufficient.

---

### Post by lagu26532 on 2021-12-11
The disk does not show up in $sudo gnome-disks.

---

### Post by sudodus on 2021-12-11
Can you

- take the disk out of the external case and test it internally in a desktop computer?

- connect the disk via a USB to SATA adapter to a USB port and check if it will get recognized as a drive?

Edit 1:

- connect the disk (start with the eSATA case and try with the other ways to connect too, if possible) to another computer and check if it will be recognized?

If none of these works, the drive is probably dead.

Edit 2:

It is possible that the problem is the electronics in the enclosure, that it is not compatible with the Linux driver of the newer kernel in Ubuntu 20.04.x LTS. Compare [this link](https://ubuntuforums.org/showthread.php?t=2469862&p=14070984#post14070984)

---

