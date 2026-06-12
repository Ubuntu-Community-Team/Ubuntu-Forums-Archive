---
title: "Disk not seen by fdisk or gparted"
date: 2016-03-21
forum: Hardware
---

### Post by Pål G. Larsson on 2016-03-21
I am running Ubuntu 15.10

A year ago I bought a fourth disk and installed as a single partion. Some time ago, it stopped working. It was still available from fdisk, but I could not mount it. Then I ran mkfs.ext4 with no errors.  Now lshw -C disk gives for the drive:
 *-disk:1
       description: SCSI Disk
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/sdd
       configuration: logicalsectorsize=512 sectorsize=4096

It gives no vendor or product information and no size

The disk is now invisible to both fdisk and gparted:

sudo fdisk /dev/sdd

Welcome to fdisk (util-linux 2.26.2).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

fdisk: cannot open /dev/sdd: "No such file or directory "(->translated to english)

This is a huge disk (3T). Is it defect? Have I used wrong tools? What can I do to figure out the issue(s)?

Pål

---

### Post by sudodus on 2016-03-21
Welcome to the Ubuntu Forums :-)

Maybe there is a GUID partition table (GPT) on the disk. When more than 2 TB, the old MSDOS partition table cannot manage it correctly. And fdisk cannot manage GPT partition tables.

Let us hope that the disk is still good, and that you can 'see it' with a modern tool. Try the following command lines:

```
sudo parted -ls  # ... space minus ell ess

sudo lsblk -fm
```

You can also check the S.M.A.R.T. information with ***smartctl***. Install, look at the manual, and run it with sudo

```
sudo apt-get install smartmontools

man smartctl
```

---

