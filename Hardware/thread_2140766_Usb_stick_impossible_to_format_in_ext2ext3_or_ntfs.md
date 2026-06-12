---
title: "Usb stick impossible to format in ext2/ext3 or ntfs, only fat32"
date: 2013-04-30
forum: Hardware
---

### Post by hardhu on 2013-04-30
Hello everybody, I have this usb stick that is driving me crazy

```
[ 3197.196096] usb 1-3: >new high-speed USB device number 6 using ehci_hcd
[ 3197.333598] usb 1-3: >New USB device found, idVendor=0718, idProduct=070a
[ 3197.333610] usb 1-3: >New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3197.333617] usb 1-3: >Product: TF10
[ 3197.333623] usb 1-3: >Manufacturer: TDK LoR
[ 3197.333629] usb 1-3: >SerialNumber: 07032BBFAE0ACB52
[ 3197.342720] scsi6 : usb-storage 1-3:1.0
[ 3198.405913] scsi 6:0:0:0: >Direct-Access     TDK LoR  TF10             PMAP PQ: 0 ANSI: 4
[ 3198.412701] sd 6:0:0:0: >Attached scsi generic sg2 type 0
[ 3200.229754] sd 6:0:0:0: >[sdb] 62529536 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 3200.231074] sd 6:0:0:0: >[sdb] Write Protect is off
[ 3200.231085] sd 6:0:0:0: >[sdb] Mode Sense: 23 00 00 00
[ 3200.232481] sd 6:0:0:0: >[sdb] No Caching mode page present
[ 3200.232490] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[ 3200.239491] sd 6:0:0:0: >[sdb] No Caching mode page present
[ 3200.239503] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[ 3200.250295]  sdb: sdb1
[ 3200.255367] sd 6:0:0:0: >[sdb] No Caching mode page present
[ 3200.255376] sd 6:0:0:0: >[sdb] Assuming drive cache: write through
[ 3200.255384] sd 6:0:0:0: >[sdb] Attached SCSI removable disk

```

It has only one fat32 partition made in windows, I would like to format it in ext2 or ext3, the process starts and it hangs a certain number of inodes (in this case 154):

```
$ sudo mkfs.ext2 /dev/sdb1
mke2fs 1.42.5 (29-Jul-2012)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
1954064 inodes, 7810816 blocks
390540 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
239 block groups
32768 blocks per group, 32768 fragments per group
8176 inodes per group
Superblock backups stored on blocks: 
   32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
   4096000

Allocating group tables: done                            
Writing inode tables: 154/239
```

and I start to see these errors in dmesg outpput:

```
[ 3874.644537] sd 3:0:0:0: >[sdb]
[ 3874.644539] Add. Sense: Write protected
[ 3874.644542] sd 3:0:0:0: >[sdb] CDB:
[ 3874.644544] Write(10): 2a 00 00 00 a8 00 00 00 08 00
[ 3874.644552] end_request: critical target error, dev sdb, sector 43008
```

repeated for a lot of times with different sectors. It seems that at a certain point the device appears to linux as if it is write-protected, but it isn't (see first code block above:  [ 3200.231074] sd 6:0:0:0: >[sdb] Write Protect is off). Then the mkfs.ext2 command complete its task, but the filesystem hasn't been created.

The same happens if try to format it in ntfs.
I have tried dozens of times with always the same result.
I have success only if I format it in fat32.

I really don't know what to do, do you think that the stick is faulty? Any suggestions on how to check it?

---

### Post by ajgreeny on 2013-04-30
Have you tried creating a new partition table on the drive then making the new partition?  Perhaps the old partition table is corrupt in some way.

Gparted is perhaps the easiest way to do this, though I presume it can be done in cli if you want; I do not know how, unfortunately, so you will need to search if that's your wish.

---

### Post by tgalati4 on 2013-04-30
Some USB stick controllers only work well in FAT32.  What is the brand and model of the USB stick?  If you can't identify it, then it might have a dodgy controller.

---

### Post by hardhu on 2013-05-01
> **ajgreeny said:**
> Have you tried creating a new partition table on the drive then making the new partition?  Perhaps the old partition table is corrupt in some way.

Gparted is perhaps the easiest way to do this, though I presume it can be done in cli if you want; I do not know how, unfortunately, so you will need to search if that's your wish.

I tried several times to build a new partition table using fdisk or even gparted, but the result after is always the same.

---

### Post by hardhu on 2013-05-01
> **tgalati4 said:**
> Some USB stick controllers only work well in FAT32.  What is the brand and model of the USB stick?  If you can't identify it, then it might have a dodgy controller.

It is written in the first block code I posted:

[ 3197.333617] usb 1-3: >Product: TF10
[ 3197.333623] usb 1-3: >Manufacturer: TDK LoR

Here's the web page for the stick:
[http://www.tdkperformance.com/en-eu/storage-media/flash-media/tf10-usb/]("http://www.tdkperformance.com/en-eu/storage-media/flash-media/tf10-usb/")

but I can't get much information about the hardware emebedded on it.

---

### Post by sudodus on 2013-05-01
Sometimes unmounting it (logically) and unplugging it (physically pulling it out) helps, so that it behaves better when reconnected. Sometimes even shutdown and cold restart of the computer helps.

It might also be an idea to clear all information, overwriting it with zeros, and then restart with gparted (device--new partition table).

```
 sudo dd if=/dev/zero of=/dev/sdx bs=4096
```

But before starting with dd, nicknamed 'disk destroyer' you need to triple check that you are writing to the correct drive (x should be a letter, typically b,c or d. Use
```
sudo fdisk -lu
```
```
sudo blkid
```
```
sudo parted -l
```
to identify the pendrive.

But the pendrive might also be broken.

---

### Post by SJR Dorset on 2013-05-01
Some USB Memory Sticks cannot support some types of partition.

---

### Post by hardhu on 2013-05-01
> **sudodus said:**
> Sometimes unmounting it (logically) and unplugging it (physically pulling it out) helps, so that it behaves better when reconnected. Sometimes even shutdown and cold restart of the computer helps.

It might also be an idea to clear all information, overwriting it with zeros, and then restart with gparted (device--new partition table).

```
 sudo dd if=/dev/zero of=/dev/sdx bs=4096
```



I have also tried to unplug/plug umount/remount it several times, and also the "brute force" solution using dd, but nothing has changed. It seems that I have already tried all what was possible to do, and that this usb stick is a crappy piece of hardware.

---

### Post by sudodus on 2013-05-01
Yes, probably it's lost, it happens quite often with pendrives. I have several of them, but mine keep working, I'm lucky so far ... I have good experiences with Sandisk and Transcend.

---

### Post by tgalati4 on 2013-05-04
The TDK website shows "Plug and Play" technology, which sounds like Windows FAT32 only.

---

### Post by davidbaumann on 2013-05-04
Did you ever use the full Capacity of the drive? Where did you buy it?
I guess it's some years ago, but there were sticks on the market sold as som GB, but only had some hundreds mbs.

But it's also possibly lost. How old is it, how much have you used it? I killed an 4GB Kingston within some weeks using it to boot my NAS, at the beginning, it also appeared as write protected sometimes.

David.

---

### Post by RJARRRPCGP on 2013-05-05
Looks like a faulty USB drive. Sorry.

---

