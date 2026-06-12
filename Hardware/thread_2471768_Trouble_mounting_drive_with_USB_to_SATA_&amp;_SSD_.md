---
title: "Trouble mounting drive with USB to SATA &amp; SSD adapter"
date: 2022-02-08
forum: Hardware
---

### Post by stoogiebuncho on 2022-02-08
Hello all,

I recently bought a USB 3.0 to SATA III & SSD Adapter so that I can transfer some data from an old hard drive (previously the /home drive of an Ubuntu install) to a new machine.

This is the device: [https://www.newegg.com/p/36F-00MF-00019?Item=9SIAPY9EDG7847](https://www.newegg.com/p/36F-00MF-00019?Item=9SIAPY9EDG7847)

Can't seem to mount anything though.  When I plug in the hard drive and connect it to my machine, I can see it in lsusb:
```
Bus 002 Device 004: ID 152d:0562 JMicron Technology Corp. / JMicron USA Technology Corp. USB3.0  Super Speed

```

But nothing pops up, and I can't see the drive in fdisk or g-parted.

I *can* see it if I go to /dev/disk/by-id, or /dev/disk/by-path, so I think it must be there somewhere.  Also, if I check dmesg, I see a number or errors but ultimately it looks like it's connecting as /dev/sda:
```
[ 4904.774651] usb 2-1: new SuperSpeed USB device number 4 using xhci_hcd
[ 4904.796073] usb 2-1: New USB device found, idVendor=152d, idProduct=0562, bcdDevice= 2.14
[ 4904.796094] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 4904.796104] usb 2-1: Product: USB3.0  Super Speed
[ 4904.796111] usb 2-1: Manufacturer: USB3.0  Super Speed
[ 4904.796117] usb 2-1: SerialNumber: DD564198838AA
[ 4904.810355] scsi host3: uas
[ 4904.812125] scsi 3:0:0:0: Direct-Access     USB3.0   Super Speed      0214 PQ: 0 ANSI: 6
[ 4904.815280] sd 3:0:0:0: Attached scsi generic sg0 type 0
[ 4904.815639] sd 3:0:0:0: [sda] Unit Not Ready
[ 4904.815657] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.815678] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.816494] sd 3:0:0:0: [sda] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4904.816514] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.816538] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.817567] sd 3:0:0:0: [sda] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4904.817590] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.817612] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.818653] sd 3:0:0:0: [sda] 0 512-byte logical blocks: (0 B/0 B)
[ 4904.818670] sd 3:0:0:0: [sda] 0-byte physical blocks
[ 4904.819655] sd 3:0:0:0: [sda] Test WP failed, assume Write Enabled
[ 4904.819855] sd 3:0:0:0: [sda] Asking for cache data failed
[ 4904.819874] sd 3:0:0:0: [sda] Assuming drive cache: write through
[ 4904.820647] sd 3:0:0:0: [sda] Optimal transfer size 33553920 bytes not a multiple of physical block size (0 bytes)
[ 4904.866868] sd 3:0:0:0: [sda] Unit Not Ready
[ 4904.866894] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.866916] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.867568] sd 3:0:0:0: [sda] Read Capacity(16) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4904.867585] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.867605] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.868257] sd 3:0:0:0: [sda] Read Capacity(10) failed: Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4904.868275] sd 3:0:0:0: [sda] Sense Key : Hardware Error [current] 
[ 4904.868304] sd 3:0:0:0: [sda] ASC=0x44 <<vendor>>ASCQ=0x81 
[ 4904.870117] sd 3:0:0:0: [sda] Attached SCSI disk

```

So it seems to be there.  But when I try to mount /dev/sda, it says "can't read superblock on /dev/sda."  When I try to mount /dev/sda1 or /dev/sda2 or any other number, it says "special device /dev/sda1 does not exist."

I've tried three different drives, and they all show the same behavior.  I can't guarantee they're all good, but I think they are, and it would be very strange if they had all gone bad since I last used them.

What are my next steps here?  Is there another way to go about mounting it?  Is it possible that it's a problem with the adapter itself?  It says linux compatible on the box, but I know that doesn't always mean it actually is.

Thanks for any tips you can provide.

---

### Post by Autodave on 2022-02-08
In gparted, top right corner, is it listed there?  You are probably not being able to mount it since it has no formatting to it.  If you can find it in gparted like I already explained, then make a partition on it and then format it.  Then you should be able to mount it.

---

### Post by stoogiebuncho on 2022-02-08
It does not show up in gparted.  Also, the drive is already formatted.

---

### Post by oldfred on 2022-02-08
Are you using the external power?
I have a USB only adapter that works well with an old SSD, but would not power up an old HDD.

---

### Post by stoogiebuncho on 2022-02-09
> **oldfred said:**
> Are you using the external power?
I have a USB only adapter that works well with an old SSD, but would not power up an old HDD.

Yep, using the included external power source.

---

### Post by Autodave on 2022-02-09
Try another USB port and see what happens.  Do not use a USB hub!  Does the drive spin up when powered?  If no spinning, adapter could very well be the issue.

---

### Post by stoogiebuncho on 2022-02-09
> **Autodave said:**
> Try another USB port and see what happens.  Do not use a USB hub!  Does the drive spin up when powered?  If no spinning, adapter could very well be the issue.

I've tried a few different USB ports.  Drives are spinning when the power is connected.

---

### Post by brrrknee on 2022-06-21
I have identical issue: original Ubuntu 20.04 LTS laptop internal 512GB SSD, partitioned with EFI *vfat*, swap, and *ext4* (system, home), working like a charm.   I pulled this SSD when changing to a new laptop.
I installed Ubuntu 22.04 LTS on the new laptop 1TB SSD.  Again working perfectly.

If I plug in the original SSD via a USB enclosure, *{ ASIDE: firstly the enclosure to 22.04 system is connecting/ disconnecting.  Until I use Disks to alter boot options to mount at startup, then the conn/ disconn loop stopped} *the SSD is  not shown, in Disks it shows *"no media" *and via *gparted*, nothing.
If I attempt the mount again, as the prior Disks action to mount at startup added a line to /etc/fstab, I get 
```
mount: /mnt/usb-External_USB3.0_dvssn-0:0: can't read superblock on /dev/sda.
```

Now this SSD worked perfectly a few days ago until I attempted to access it as an external, USB drive with lots of important data I had built up, across several *ext4* partitions.

If there are any mysterious actions I need to take in order to access the prior internal "hard drive" SSD as an additional drive, please help me to understand and if I missed a step, I'll remember next time around.

Thank you in advance.

---

