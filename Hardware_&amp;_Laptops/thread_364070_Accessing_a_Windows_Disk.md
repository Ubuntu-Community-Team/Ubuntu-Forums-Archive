---
title: "Accessing a Windows Disk"
date: 2007-02-17
forum: Hardware &amp; Laptops
---

### Post by leatherworker on 2007-02-17
Hi there,

I am fairly new on Ubuntu 6.10.  

In Short - My previous motherboard burnt up - I rebuilt the machine and installed Ubuntu on an empty 30Gb drive - everything running fairly smooth.

Now I connected the 80Gb drive I used to have on my Windows machine and that had all my data on (it was not a boot disk).  

My first question - how do I get to access the documents and photos I have on that disk - the documents are Open Office dicuments?

My second question has to do with the partitioning on my Ubuntu disk:  This is what Gparted tells me about the partitioning on that disk:
/dev/hda1/    ext3    35GiB       2.9GiB used     Flag is   Boot
/dev/hda2/   extended   1.4GiB
/dev/hda5/   linux-swap  1.4GiB

Should I somehow try to improve this situation for better performance?

Is the whole 30GiB disk available to me?

JOhan

---

### Post by kidders on 2007-02-17
Hi there,

> **leatherworker said:**
> My first question - how do I get to access the documents and photos I have on that disk - the documents are Open Office dicuments?You could start by using **fdisk -l** to identify the /dev nodes for your partitions on the other disk (eg /dev/hdb1, /dev/hdb2). Create somewhere to put them (eg /mnt/windows1, /mnt/windows2) and mount them manually. Once you find a nice set of mount options, that makes your filesystems behave the way you want them to, you could use /etc/fstab to store them, or have your filesystems automatically mounted in the future.

> **leatherworker said:**
> Should I somehow try to improve this situation for better performance?Theoretically, putting swap in an extended partition is not optimal, although whether that really makes any perceptible difference is debatable. One other tweak you might consider is putting your /home on a separate partition. Keeping your personal files separate from the OS has certain advantages, but is certainly not essential.

---

### Post by leatherworker on 2007-02-18
Thanks for your great help!

I have spent the whole morning learning as much as I can about mounting and the fstab parameters.

But I got stuck on a basic problem:

I tried to mount manually with 
sudo mount -t ext3 /dev/hdb1 /mnt/second
and as variations I tried hdb,  hdb2  (although I know that windows disk only had one partition on it).
The responce I get each time is:

" wrong fs type, bad option, bad superblock on /dev/hdb2,
       missing codepage or other error
       (aren't you trying to mount an extended partition,
       instead of some logical partition inside?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so"

When I do the dmesg, I get :

johan@johan-desktop:/$ dmesg | tail
[17179631.648000] Bluetooth: RFCOMM socket layer initialized
[17179631.648000] Bluetooth: RFCOMM TTY layer initialized
[17179631.648000] Bluetooth: RFCOMM ver 1.7
[17179641.680000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17229479.172000] VFS: Can't find an ext2 filesystem on dev hdb1.
[17229598.368000] VFS: Can't find ext3 filesystem on dev hdb1.
[17229615.020000] VFS: Can't find ext3 filesystem on dev hdb.
[17229705.760000] attempt to access beyond end of device
[17229705.760000] hdb2: rw=0, want=4, limit=2
[17229705.760000] EXT3-fs: unable to read superblock

It looks as though I should not use ext3.  This one has me stumped.

Johan

---

### Post by kidders on 2007-02-18
> **leatherworker said:**
> wrong fs type, bad option, bad superblock on /dev/hdb2This normally means the filesystem is not an Ext3 one. Since you mentioned Windows, this fairly likely, since Microsoft doesn't support the Linux Extended filesystems (Ext2/3).

> **leatherworker said:**
> [17229705.760000] EXT3-fs: unable to read superblockNo superblock = No Ext2/3 filesystem.

If you don't know the filesystem type, leave out the **-t** option to have Linux auto-detect it.

---

