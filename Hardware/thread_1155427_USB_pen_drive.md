---
title: "USB pen drive"
date: 2009-05-10
forum: Hardware
---

### Post by Danielkida on 2009-05-10
Hi, This is not a problem with ubuntu in any way, but it's annoying all the same.

I got some free usb sticks at a fayre from the local police stall. They are really nice..1gb. However there is a problem with them.

They mount as 2 seperate partitions (they do this on windows as well).
One mounts as a usb as normal and the other thinks its a cdrom, what makes it worse is that there is an autorun that launches a power point presentation of their crime figures!
Interesting reading once, but i don't want it to autorun and try and load powerpoint everytime i plug it into a windows computer!! especially at the library etc..you are talking 20 minutes for that to load!!

It's a shame, as It feels a waste to throw them away, but they are unusable now to me or my friends. I don't know why they would do this!

I was wondering if anyone else had seen this before? or if there is a way I can just format them to just be a usb drive?

Thanks
Daniel

---

### Post by sgosnell on 2009-05-10
Open gparted, remove all the partitions, add a new partition full-size, format, and you're set.

---

### Post by Danielkida on 2009-05-10
> **sgosnell said:**
> Open gparted, remove all the partitions, add a new partition full-size, format, and you're set.

Unfortunately the partition isn't visible to gparted. But it does appear to be mounted, as an icon appears on the desktop.

right clicking and selecting properties tells me:
label:20080926_1110
Size :912.0KB
Media:CD-ROM Disk
File System: iso9660 (Joliet Extension)

Anything else I can try? any heavy handed linux commands to force it?

I think the problem is that it sees the two partitions as separate devices, as one mounts at /media/20080926_1110 and the one it sees as a usb drive mounts at /media/sdb, if that helps.

---

### Post by cosine352 on 2009-05-10
> sudo fdisk -l
find the name of the disk for the pendrive. Say for example it is 'sdx'

> sudo umount /dev/sdx
fdisk /dev/sdx

type 'm' for the usable commands. 
make sure to chose the proper partition.

---

### Post by sgosnell on 2009-05-10
You need to unmount all the partitions before you can manipulate them.  It appears the 'CD' is just a .iso, which you should be able to delete.  Try running gparted, selecting the partition you see, and see what the size is.  If it's close to 1GB, you can probably just format the partition as FAT32 and recover everything.  It won't be exactly 1GB, probably .9-something.

---

### Post by Danielkida on 2009-05-11
It's very strange. gparted can't see the cd partition and it doesn't show up in fdisk -l either i just get
```
Disk /dev/sdb: 1045 MB, 1045282816 bytes
2 heads, 63 sectors/track, 16202 cylinders
Units = cylinders of 126 * 512 = 64512 bytes
Disk identifier: 0x0007c503

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       16203     1020768    b  W95 FAT32

```
I've tried formatting it into numerous file systems, yet the space being used is always above about 1.6MB.

Any other commands I can try?

---

### Post by megamania on 2009-05-11
> **Danielkida said:**
> Any other commands I can try?
Did you try what the other suggested?

- plug the usb stick in
- when it's mounted, unmount it (right click on it, select unmount)
- when it's unmounted, leave it inserted 
- run Gparted
- remove all partitions (looks like there's only one though)
- create a new FAT32 partition
- format the partition
- apply changes

---

### Post by Danielkida on 2009-05-11
I tried dmesg, and it showed that it was mounting a cd-rom at /dev/sr1

I tried to format this with fdisk but got:
```
You will not be able to write the partition table.
Note: sector size is 2048 (not 512)
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x9f103c9f.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.

You must set cylinders.
You can do this from the extra functions menu.
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```

If I try to write it says unable to write and exits.

And yeah, formatting it with gparted was the first thing I tried. It appears to work correctly, but after removing and plugging in again, it still mounts a cd drive as well.

---

### Post by Danielkida on 2009-05-11
This is the output of dmesg when plugging in the device.

```
[ 1686.864066] usb 1-1: new high speed USB device using ehci_hcd and address 4
[ 1687.016396] usb 1-1: configuration #1 chosen from 1 choice
[ 1687.040216] scsi4 : SCSI emulation for USB Mass Storage devices
[ 1687.041632] usb-storage: device found at 4
[ 1687.041636] usb-storage: waiting for device to settle before scanning
[ 1692.040188] usb-storage: device scan complete
[ 1692.040675] scsi 4:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[ 1692.041039] scsi 4:0:0:1: CD-ROM            CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[ 1692.075535] sd 4:0:0:0: [sdb] 2041568 512-byte hardware sectors: (1.04 GB/996 MiB)
[ 1692.079587] sd 4:0:0:0: [sdb] Write Protect is off
[ 1692.079591] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1692.079594] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1692.082327] sd 4:0:0:0: [sdb] 2041568 512-byte hardware sectors: (1.04 GB/996 MiB)
[ 1692.083397] sd 4:0:0:0: [sdb] Write Protect is off
[ 1692.083401] sd 4:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[ 1692.083404] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 1692.083410]  sdb: sdb1
[ 1692.085122] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 1692.085198] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 1692.089894] sr1: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
[ 1692.090013] sr 4:0:0:1: Attached scsi CD-ROM sr1
[ 1692.090087] sr 4:0:0:1: Attached scsi generic sg3 type 5
[ 1692.227240] __ratelimit: 30 callbacks suppressed

```

---

### Post by megamania on 2009-05-11
> **Danielkida said:**
> And yeah, formatting it with gparted was the first thing I tried. It appears to work correctly, but after removing and plugging in again, it still mounts a cd drive as well.
I googled for your problem and found this:
[http://forum.eeeuser.com/viewtopic.php?id=32191](http://forum.eeeuser.com/viewtopic.php?id=32191)

I think that clarifies it.

---

### Post by Danielkida on 2009-05-11
Thanks,

The final post fixed it.
However the program in windows destroyed the partition table and couldn't format it.
Luckily i booted back into ubuntu, rewrote the allocation table with fdisk and then was able to reformat with gparted. Phew!

It just seems immoral that any company would put this on to autorun! Without giving an (easy) option to remove it.

Anyway,
Solved
Thankyou

---

### Post by megamania on 2009-05-11
> **Danielkida said:**
> 
Solved
Thankyou
Glad I could help.

Just so you know, I googled part of your dmesg to find the solution:
```

"CD-ROM            CBM      Flash Disk       5.00 PQ: 0 ANSI: 2"

```

---

