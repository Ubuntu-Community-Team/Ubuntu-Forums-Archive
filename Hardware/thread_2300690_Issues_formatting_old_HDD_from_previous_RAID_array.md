---
title: "Issues formatting old HDD from previous RAID array (mdadm)"
date: 2015-10-27
forum: Hardware
---

### Post by LastHylian on 2015-10-27
I have two 1TB HDDs from an old RAID array I'd like to format for general storage, but neither Linux or my Windows box can mount the drive. Linux is able to see the drive, but I am unable to format it or zero it out. When I try, I receive the following message:

```
failed to open &#8216;/dev/sdb&#8217;: No medium found
```

Is the MBR screwed? Any way to recover?

Thanks in advance!

---

### Post by weatherman2 on 2015-10-27
What command are you using to try to do this?

What's the output of these commands:

```

sudo fdisk -l
sudo parted -l

```

?

Are you sure these drives are good?  Checked S.M.A.R.T. status/attributes?

---

### Post by LastHylian on 2015-10-27
Sorry forgot to mention the command. Was trying to zero it out with **dd if=/dev/zero of=/dev/sdb bs=8M**
Here's some more relevant info below.

# fdisk -l
```
Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x000ad993

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 246071295 246069248 117.3G 83 Linux
/dev/sda2       246073342 250068991   3995650   1.9G  5 Extended
/dev/sda5       246073344 250068991   3995648   1.9G 82 Linux swap / Solaris
```


# parted -l
```
Model: ATA KINGSTON SVP100S (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  126GB  126GB   primary   ext4            boot
 2      126GB   128GB  2046MB  extended
 5      126GB   128GB  2046MB  logical   linux-swap(v1)
```

# dmesg
```
[10986.507539] usb-storage 1-11:1.0: USB Mass Storage device detected
[10986.507726] scsi host8: usb-storage 1-11:1.0
[10987.507892] scsi 8:0:0:0: Direct-Access     SPIF30x  USB2SATA Bridge  0132 PQ: 0 ANSI: 2
[10987.508150] sd 8:0:0:0: Attached scsi generic sg1 type 0
[10987.509179] sd 8:0:0:0: [sdb] Attached SCSI removable disk
```

# ls -la /dev/sd*
```
brw-rw---- 1 root disk 8,  0 Oct 27 20:21 /dev/sda
brw-rw---- 1 root disk 8,  1 Oct 27 20:21 /dev/sda1
brw-rw---- 1 root disk 8,  2 Oct 27 20:21 /dev/sda2
brw-rw---- 1 root disk 8,  5 Oct 27 20:21 /dev/sda5
brw-rw---- 1 root disk 8, 16 Oct 27 19:40 /dev/sdb
```

**EDIT** Forgot to mention I can't do a SMART check either since I cannot sense the HDD.

---

