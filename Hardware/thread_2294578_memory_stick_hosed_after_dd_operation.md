---
title: "memory stick hosed after dd operation?"
date: 2015-09-11
forum: Hardware
---

### Post by Greg_Larkins on 2015-09-11
I attempted to write an img file to an 8GB usb memory stick using dd

$ sudo dd if=myimagefile.img of=/dev/sdb bs=1M

which results in:

94+1 records in
94+1 records out
99293159 bytes (99 MB) copied, 0.0800921 s, 1.2 GB/s

but the command runs instantaneously, and nothing appears to be copied to the memory stick. The stick no longer appears in Nemo even after unplugging and re-plugging.

GParted shows:
Partition: unallocated
File system: unallocated
Size: 94.69 MiB

If I try to create a new partition on the stick, it fails with error: '/dev/sdb1: No such file or directory'

and GParted now shows:
Partition: /dev/sdb1
File system: unknown
Size: 93.00 MiB

fdisk -l shows:

Disk /dev/sdb: 99 MB, 99292672 bytes
4 heads, 32 sectors/track, 1515 cylinders, total 193931 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000479d2


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      192511       95232    b  W95 FAT32

I have googled around for hours but can't seem to find a solution. Is my stick now dead? I really liked that stick, expensive fast one and not that old :(

---

### Post by QDR06VV9 on 2015-09-11
I have run into that myself.
But no worries just use Gparted to reformat.
Disks never worked for me just Gparted.
Hope that helps

---

### Post by Greg_Larkins on 2015-09-11
ok so I go back to this step:

[COLOR=#000000]GParted shows:[/COLOR]
[COLOR=#000000]Partition: unallocated[/COLOR]
[COLOR=#000000]File system: unallocated[/COLOR]
[COLOR=#000000]Size: 94.69 MiB

and run Device -> Create Partition Table...
and select msdos partition type and Apply

then Partition -> New
and select Primary Partition and fat32
then click Add and Apply
then click the green tick to really apply...

this results in '[/COLOR]An error occurred while applying the operations see the details for more information'

when I check the details that's when I see the '/dev/sdb1: No such file or directory' error

and GParted now reports

[COLOR=#000000]and GParted now shows:[/COLOR]
[COLOR=#000000]Partition: /dev/sdb1[/COLOR]
[COLOR=#000000]File system: unknown[/COLOR]
[COLOR=#000000]Size: 93.00 MiB[/COLOR]

---

### Post by Greg_Larkins on 2015-09-11
Interestingly, if I use Ubuntu's inbuilt 'Disks' program it sees the drive and reports the correct size of 7.9GB.

But if I try to use 'Disks' to format the drive, it gives an error: 'Error formatting disk Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)'

If that gives any clues?

---

### Post by QDR06VV9 on 2015-09-11
Sorry I forgot to tell you to burn Gparted to disk or usb and then boot to gparted and And plugin your hosed USB and Format away
 all should be good to go from there. 
Gparted iso [http://distrowatch.com/?newsid=09050](http://distrowatch.com/?newsid=09050)
Regards

---

### Post by Greg_Larkins on 2015-09-11
oh lord... yes runrickus thanks for the memory jog... I booted off my trusty [System Rescue CD]("http://www.sysresccd.org/") and ran gparted from there - all good
(link provided for anyone looking for a great tool)

---

### Post by efflandt on 2015-09-11
You have not said what sort of iso you wrote to it. I once formatted a floppy as a Mac disk instead of MS DOS disk back when Linux used minix to boot from an MS DOS formatted floppy. But as a Mac disk it had something on it such that I could no long format it for MSDOS. So I used dd to write a bunch of /dev/zero to the floppy and then I was able to MSDOS format it.

So I would suggest writing 100 MB of zeros to the memory stick:```
sudo dd bs=4M count=25 if=/dev/zero of=/dev/sdb
```Then see if you can add an msdos partition table with gparted and create a FAT32 partition.

---

### Post by Greg_Larkins on 2015-09-12
It was a pfsense spin for memory sticks, so BSD format. I got around that problem by downloading the spin for CD, and installed off that.

Back to the memory stick, your solution to boot gparted - or in my specific case, a rescue disk with gparted included - worked fine. I had tried variations of dd found on various forums, but nothing worked for me. I am therefore loath to experiment again, although I suppose I should while problem is still fresh in my mind....

---

### Post by sudodus on 2015-09-12
***dd*** is nicknamed 'disk destroyer' because it does what you tell it to do without questions, even if you tell it to overwrite the drive with your family pictures. (A minor typing error is enough for this to happen, and I have seen too many threads at the Ubuntu Forums asking for help to save what can be saved after such accidents.)

You can wrap security around dd with [mkusb](https://help.ubuntu.com/community/mkusb). The main task for it is installing from **iso** files, **img** files and compressed image **img.gz** and **img.xz** files. But mkusb can also be used to ***wipe the first megabyte*** (actually mibibyte), which is often enough to refresh a drive so that ***gparted*** will manage to create a new partition table.

---

