---
title: "BIOS recognizes my HDD, but lsblk does not."
date: 2023-03-08
forum: Hardware
---

### Post by stevermann on 2023-03-08
[SIZE=2][FONT=arial]I have Ubuntu 20.04.2 LTS installed on a BMAX Mini PC.  Works just fine,
I added a 2.5 inch SATA SSD, and BIOS recognizes it.
But [COLOR=#5A7425][FONT=arial black]sudo lsblk -e7[/FONT] doesn't see the disk.

The disk is a 64Gb SSD formatted as NTFS and works fine in a Windows PC.

Any ideas of how to mount this disk would be appreciated.[/COLOR][/FONT][/SIZE]

---

### Post by stevermann on 2023-03-09
Update. Formatting as Ext4 fixed everything

---

### Post by yancek on 2023-03-09
If the drive was formatted as ntfs and was being used on a windows OS, recent releases of windows use hibernation by default and if the system was in a state of hibernation when youu removed it from the windows PC, it would not be mounted and accessible from Linux due to the high risk of loss of data.  Just a guess.

---

