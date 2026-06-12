---
title: "missing/corrupt hd"
date: 2007-02-11
forum: Hardware &amp; Laptops
---

### Post by zetman on 2007-02-11
I've got a hard drive that stopped mounting properly.  It would cause the computer to stop booting, so I commented it out of /etc/fstab.  Now I can't figure out how to fix it because I can't find where a back up superblock would be.  I posted the output of the commands I've tried below.  I'm at a bit of loss as to what to do next.

```
zetman@Zetman:~$ sudo dumpe2fs /dev/hdb2
dumpe2fs 1.38 (30-Jun-2005)
dumpe2fs: No such file or directory while trying to open /dev/hdb2
Couldn't find valid filesystem superblock.
```

```
zetman@Zetman:~$ mke2fs -n /dev/hdb2
mke2fs 1.38 (30-Jun-2005)
Could not stat /dev/hdb2 --- No such file or directory

The device apparently does not exist; did you specify it correctly?
```


Output from: ```
sudo fdisk -l
```

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          24      192748+  83  Linux
/dev/hda2              25       19457   156095572+   5  Extended
/dev/hda5              25       19457   156095541   8e  Linux LVM

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          13      104391   83  Linux
/dev/hdb2              14       14524   116559607+  83  Linux
/dev/hdb3           14525       14593      554242+  83  Linux
```

As you can see, /dev/hdb2 is listed, but 

```
zetman@Zetman:~$ l /dev | grep hd
lrwxrwxrwx 1 root root           3 2007-02-11 06:36 cdrom -> hdd
lrwxrwxrwx 1 root root           3 2007-02-11 06:36 cdrw -> hdc
lrwxrwxrwx 1 root root           3 2007-02-11 06:36 dvd -> hdd
brw-rw---- 1 root disk      3,   0 2007-02-11 06:36 hda
brw-rw---- 1 root disk      3,   1 2007-02-11 06:36 hda1
brw-rw---- 1 root disk      3,   2 2007-02-11 06:36 hda2
brw-rw---- 1 root disk      3,   5 2007-02-11 06:36 hda5
brw-rw---- 1 root disk      3,  64 2007-02-11 06:36 hdb
brw-rw---- 1 root cdrom    22,   0 2007-02-11 06:36 hdc
brw-rw---- 1 root cdrom    22,  64 2007-02-11 06:36 hdd
```

Output from: ```
sudo dmesg | grep hdb
```

```
[17179572.640000]     ide0: BM-DMA at 0xa800-0xa807, BIOS settings: hda:DMA, hdb:DMA
[17179573.336000] hdb: WDC WD1200BB-18CAA0, ATA DISK drive
[17179575.192000] hdb: max request size: 128KiB
[17179575.192000] hdb: Host Protected Area detected.
[17179575.196000] hdb: Host Protected Area disabled.
[17179575.196000] hdb: 234441648 sectors (120034 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.196000] hdb: cache flushes not supported
[17179575.196000]  hdb:hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.200000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.200000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.200000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.204000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.204000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.204000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.204000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.256000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.256000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.260000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.260000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.260000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.260000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.264000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.264000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.316000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.316000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.316000] end_request: I/O error, dev hdb, sector 0  I'm not new to computer's, but I am a bit new to Linux.
[17179575.316000] Buffer I/O error on device hdb, logical block 0
[17179575.316000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.316000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.316000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.316000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.320000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.320000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.320000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.320000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.376000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.376000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.376000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.376000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.380000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.380000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.380000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.380000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.432000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.432000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.432000] end_request: I/O error, dev hdb, sector 0
[17179575.432000] Buffer I/O error on device hdb, logical block 0
[17179575.468000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.468000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.492000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.492000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.544000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.544000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.544000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.544000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.676000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.676000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.704000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.704000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.756000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.756000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
[17179575.756000] hdb: dma_intr: status=0x51 { DriveReady SeekComplete Error }
[17179575.756000] hdb: dma_intr: error=0x84 { DriveStatusError BadCRC }
```

I not sure what any of that last one means, but it doesn't look good.  Also, testdisk only found /dev/hdc.  I've been searching the forums for similar posts, but I haven't found anything that worked for me.  I really need to get at the files on this hard drive ASAP because I need them to write a report.  Thanks for any help.

---

