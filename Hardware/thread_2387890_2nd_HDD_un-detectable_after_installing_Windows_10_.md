---
title: "2nd HDD un-detectable after installing Windows 10 in parallel"
date: 2018-03-25
forum: Hardware
---

### Post by simoncks1994 on 2018-03-25
Hi everyone,

I built a workstation with two HDD. The first has Ubuntu 16.04 installed. I intend to reserve 200Gb in the second disk for Windows 10 while the rest is still unallocated space. I partitioned and installed Windows 10 successfully.

Now I boot "try Ubuntu" with USB to update the GRUB (reference: 2nd reply in the [post]("https://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu")). I get back my GRUB screen, but still an error returns:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key
```

A check in "try Ubuntu" indicates there is only one harddrive recognisable. The same applies to Gparted. Disconnecting the 2nd harddisk does not help.

```
Disk /dev/loop0: 1.5 GiB, 1564921856 bytes, 3056488 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 38DA3458-5923-4B2A-95C4-E8F0B77C621B


Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1023999   1021952   499M Windows recovery environment
/dev/sda2  1024000   1228799    204800   100M EFI System
/dev/sda3  1228800   1261567     32768    16M Microsoft reserved
/dev/sda4  1261568 419432447 418170880 199.4G Microsoft basic data








Disk /dev/sdb: 7.4 GiB, 7969177600 bytes, 15564800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0004d5f9


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 15564799 15562752  7.4G  c W95 FAT32 (LBA)

```

Is there anything I could do to recover the disk? Thanks in advance.

Simon

---

### Post by simoncks1994 on 2018-03-25
A recheck reveals that I forgot to connect my 1st harddisk after Windows 10 installation...

---

### Post by oldfred on 2018-03-25
With two drives it sometimes is easier to disconnect the other drive.
Be sure to connect drives in SATA port order starting with SATA0.
But then you may have to recreate UEFI entries for booting. Usually UEFI finds Windows entries, but does not find any others, so you have to use efibootmgr to restore a boot entry.

But partition in advance with gpt and include an ESP on Ubuntu drive. Generally Ubuntu only uses the sda drive or first drive's ESP, but I copy entries from sda's ESP to sdb's ESP as backup. And with efibootmgr could make those work.

What brand motherboard & what video card/chip?
Some require boot parameters to work or work well.

---

### Post by simoncks1994 on 2018-04-05
I think I will stick with it meanwhile. I hope not to touch on it again to complicate the problem.

Motherboard info :
```
sudo dmidecode -t 2
Manufacturer: Gigabyte Technology Co., Ltd.
Product Name : B85M-D3H
```

My GPU model is GeForce GTX 750 Ti.

---

