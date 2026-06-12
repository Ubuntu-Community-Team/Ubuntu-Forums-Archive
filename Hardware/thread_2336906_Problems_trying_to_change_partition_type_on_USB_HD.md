---
title: "Problems trying to change partition type on USB HD"
date: 2016-09-12
forum: Hardware
---

### Post by frankvw2 on 2016-09-12
Using Ubuntu 12.04LTS, I have reformatted a 2TB USB harddisk that had originally been formatted on a Windows XP box and therefore had NTFS on it. So. Right-click, format to EXT4, and all should be well. Right?

No. Not quite. Now Palimpsest tells me that the file system type is still **HPFS/NTFS (0x07)** which makes sense when you think about it (too late) because I did reformat the disk but never thought to change the partition. I simply plonked an EXT4 file system on it, then proceeded to fill the disk with 2TB of data, which took about 36 hours because all I have is USB2.0.

Palimpsest's option to edit the partition type to **Linux (0x83)** looked hopeful, but unfortunately when Palimpsest spawns udisks-helper-modify-partition, the latter starts properly:

[FONT=courier new]$ ps -ef | grep sdb
udisks-helper-modify-partition /dev/sdb 1048576 2000396746752 0x83  
[/FONT]
but then sits there in an infinite loop, hogging the CPU and doing nothing else, and it won't budge without dynamite (i.e. kill -9). This appears to be a known bug (source: [http://bugs.launchpad.net/bugs/694060](http://bugs.launchpad.net/bugs/694060) and [http://github.com/midenok/stuff-linux/issues/2](http://github.com/midenok/stuff-linux/issues/2)) which has persisted for about four years now.

So I tried to use fdisk. After umounting /dev/sdb:

[FONT=courier new]$ fdisk /dev/sdb
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xde3acdbf.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

Disk /dev/sdb1: 2000.4 GB, 2000396746752 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907024896 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xde3acdbf

     Device Boot      Start         End      Blocks   Id  System

Command (m for help): q[/FONT]

So fdisk complains about a missing disk label and an invalid partition flag, presumably attempts to correct it (in memory) and then hands me an empty partition table. Using fdisk -l to list the partition table *does* show me the NTFS partition, though:

[FONT=courier new]$ fdisk -l /dev/sdb
Disk /dev/sdb: 2000.4 GB, 2000398931968 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029164 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x882d225a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT[/FONT]

Obviously I'm overlooking something here. Fdisk can list the partitions on the disk and display the one that is there, but in interactive mode which I need to change the partition type to **Linux (0x83)** it borks and presumes there are no (valid) partitions at all.

What am I missing? How do I edit this partition type from 7 in to 83 so the partition type matches the EXT4 file system it contains?

All suggestions appreciated!

// FvW

---

### Post by sudodus on 2016-09-12
Welcome to the Ubuntu Forums :-)

After changing things in the partition table, the kernel will not always recognize the changes until you have rebooted the computer. So that would be my first tip: Please reboot.

You can also try different tools. I prefer ***gparted***. It comes with the Ubuntu iso files, and is available in the live session, when booted from the install DVD or USB drive, 'Try Ubuntu'. It is possible to install gparted into an installed system too,

```
sudo apt-get install gparted
```

Run it from the dash or the menu. If you want to reformat the whole drive, I suggest that you start by selecting

[LIST]
[*]*** the correct drive*** (in the top right corner of the gparted window).
[*]Then select ***Device -- Create partition table***
 [LIST]
 [*]MSDOS is the old style partition table, but I suggest that you try the new GUID partition table, GPT. Learning to use it is good, because next time you might get a drive with more than 2 TB, and then you need GPT in order to use the whole drive.
 [/LIST]
[*]After that you can ***work graphically*** by right-clicking etc. The interface of gparted is eary to use.
[*]When you are happy with the configuration, please ***click on the tick icon*** to start the action.
[/LIST]

If you still have problems, I suggest that you wipe it with mkusb. See these links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

---

### Post by frankvw2 on 2016-09-12
Thanks, Sudodus! All these are good suggestions.

However, my fdisk issue turned out to be much more basic. I typed 'fdisk' where I should have typed 'sudo fdisk'. In other words, it was a privileges issue that caused fdisk to come up with a rather misleading (and at the very least unhelpful) error message. Running fdisk as root solved the problem.

Duh!

Anyway. Thanks for your suggestions, they are sensible and good ones!

// FvW

---

### Post by sudodus on 2016-09-12
Congratulations and thanks for sharing your solution (and marking the thread as solved) :-)

---

