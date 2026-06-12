---
title: "Problem with FAT32 USB Sticks"
date: 2013-01-12
forum: Hardware
---

### Post by SillySod on 2013-01-12
I have a number of old-ish 1GB USB sticks which work fine in Windows and show up as formatted to FAT 32.

As soon as I put them in Ubuntu machine (even the same machine as the Windows machine with dual OS) they stop working.  I have tried in 3 different Ubuntu machines, 10.04 and 12.04 and I can't get them to work.

They don't mount automatically and don't show up using "mount -l".

GParted just stays "Scanning all devices" forever, using "sudo fdisk -l" or "sudo sfdisk -l" report the hard disc but don't get any further.  Something I read told me to find out things using "sudo blkid" but nothing happens with this.

Using disc utility, the USB stick eventually shows up under "Peripheral devices...Generic Flash disc" but clicking on it says it is not partitioned and shows an "unknown" volume of 1GB.

Am I missing some kind of FAT32 driver or doing something else wrong?

---

### Post by ahallubuntu on 2013-01-12
Any chance they are encrypted?

FAT32 should work out of the box in Ubuntu.

Right after you plug one in, type "dmesg" in a terminal and see if anything related to your USB stick shows up there.

---

### Post by SillySod on 2013-01-12
This is what I got at the end of dmesg:
```

[ 5092.436141] usb 1-1: new high-speed USB device number 14 using ehci_hcd
[ 5092.665049] scsi15 : usb-storage 1-1:1.0
[ 5093.666493] scsi 15:0:0:0: Direct-Access     Generic  Flash Disk       8.00 PQ: 0 ANSI: 2
[ 5093.669801] sd 15:0:0:0: Attached scsi generic sg1 type 0
[ 5093.673083] sd 15:0:0:0: [sdb] 1966080 512-byte logical blocks: (1.00 GB/960 MiB)
[ 5093.675455] sd 15:0:0:0: [sdb] Write Protect is off
[ 5093.675476] sd 15:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 5093.676155] sd 15:0:0:0: [sdb] No Caching mode page present
[ 5093.676174] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 5093.680939] sd 15:0:0:0: [sdb] No Caching mode page present
[ 5093.680959] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 5093.694788]  sdb:
[ 5093.697517] sd 15:0:0:0: [sdb] No Caching mode page present
[ 5093.697526] sd 15:0:0:0: [sdb] Assuming drive cache: write through
[ 5093.697535] sd 15:0:0:0: [sdb] Attached SCSI removable disk

```

How could I tell if it's encrypted?  Does Windows do that when it formats a USB stick?

---

### Post by ahallubuntu on 2013-01-12
No, Windows doesn't automatically encrypt anything, but some USB sticks come with software included that encrypts the partition.

What happens if you type

```
sudo fdisk -l
```

Anything show up for /dev/sdb ?

---

### Post by SillySod on 2013-01-12
Nothing happens with fdisk, it reports /dev/sda and then I just get a flashing cursor forever.

---

### Post by ahallubuntu on 2013-01-12
After about 10 seconds of the "flashing cursor," hit Ctrl-C to end the attempt to do fdisk, and then check dmesg again and see if anything is shown there.

I hear of compatibility issues like this once in a while with USB sticks in Ubuntu but I've personally never had one.

---

### Post by SillySod on 2013-01-12
CTRL-C didn't break out of it, but CTRL-Z did.  I think this is the new bit of dmesg:
```

[ 6517.200140] usb 1-1: reset high-speed USB device number 17 using ehci_hcd
[ 6548.176094] usb 1-1: reset high-speed USB device number 17 using ehci_hcd
[ 6579.152074] usb 1-1: reset high-speed USB device number 17 using ehci_hcd
[ 6610.128089] usb 1-1: reset high-speed USB device number 17 using ehci_hcd
[ 6610.352043] sd 18:0:0:0: [sdb] Media Changed
[ 6610.352052] sd 18:0:0:0: [sdb]  Result: hostbyte=DID_ABORT driverbyte=DRIVER_SENSE
[ 6610.352061] sd 18:0:0:0: [sdb]  Sense Key : Unit Attention [current] 
[ 6610.352070] Info fld=0x0
[ 6610.352075] sd 18:0:0:0: [sdb]  Add. Sense: Not ready to ready change, medium may have changed
[ 6610.352086] sd 18:0:0:0: [sdb] CDB: Read(10): 28 00 00 1d ff f8 00 00 01 00
[ 6610.352106] end_request: I/O error, dev sdb, sector 1966072
[ 6610.352116] Buffer I/O error on device sdb, logical block 245759
[ 6610.355789] sd 18:0:0:0: [sdb] No Caching mode page present
[ 6610.355802] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[ 6610.358426] sd 18:0:0:0: [sdb] No Caching mode page present
[ 6610.358441] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[ 6610.370410]  sdb:
```

---

### Post by SillySod on 2013-01-12
I just tried to format it in Disc Utility, but an error came up saying

"An error occurred while performing an operation on Generic Flash Disc: The daemon is being inhibited".

The same error also comes up if I try power down, benchmark read only or benchmark read/write.

---

### Post by Merrattic on 2013-01-12
Do the ones you have tried still work on Windows or are they now corrupt.

Try removing the data (if you need it) and then reformat (to FAT32/NTFS) see if that sorts it.

I remember having a similar problem years ago, and this sorted it out for me.

---

### Post by SillySod on 2013-01-13
I did reformat one of them in Windows to FAT32 (actually it was FAT beforehand) but it didn't help.  I'll try to format it to NTFS and see if that helps.

---

### Post by SillySod on 2013-01-13
I didn't get an option for NTFS in Win XP, just FAT or FAT32.  Is this telling me it's ancient hardware which should be scrapped, or is there a way of doing it from command line?

---

### Post by Merrattic on 2013-01-15
Try with gparted (formatting to ntfs that is), or also to fat32.

---

### Post by SillySod on 2013-01-21
I've discovered 2 things, these appear to have helped.

The first thing is that the allocation unit was 32KB, I thought that was a bit much, so I set it to 512 bytes.

The other thing is that if I format one of the sticks at work and turn off a thing which I think was called "ReadyBoost" ?!?! then it does work in Ubuntu.  We have a later version of Winxxxx at work than at home (XP at home).  I didn't get this option at home.

I don't think the allocation unit issue fixed it on its own, because I tried to format one of the sticks at home from the DOS command line and although it worked, trying to access it from the explorer thing crashed the whole of Windows!

I presume that these sticks were formatted at work with the default settings and it must be necessary to re-format them in the same operating system version to clear it all off.

---

### Post by coldraven on 2013-01-21
I use some old 1GB SD cards I use for making Live CDs into bootable USB drives.
I am constantly trying new distros and have never had a problem with them.
In gparted the first thing I do is select "Delete Partition".
Then "Create new partition"
Then format, usually FAT32.
Maybe that way will help get rid of your problem.

Edit: FWIW I had to update the BIOS on a netbook recently and it would only work with a USB stick less than 512MB formatted  with FAT16 .
I only had a 8GB stick but deleting the partition, creating one of 256MB FAT16 and leaving the rest as "Unallocated" worked fine.
I then reverted it back to 8GB NTFS.
I love gparted :)

---

### Post by SillySod on 2013-01-21
The trouble is, I don't get as far as being able to see the stick in GParted or Disc Utility, or even in mount, fdisk etc. - it seems that whatever is on these sticks when I first try them causes them to be invisible to the whole of Ubuntu (except in dmesg)!!

---

### Post by SillySod on 2013-02-14
I tried another one at work, I formatted it to NTFS with a file allocation size of 4096 bytes and that worked straight off on Ubuntu.

I still don't understand why these sticks are still "inaccessible" in Ubuntu until they are re-formatted in Windows.

---

