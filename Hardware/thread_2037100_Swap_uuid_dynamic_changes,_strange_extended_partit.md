---
title: "Swap uuid dynamic changes, strange extended partition"
date: 2012-08-03
forum: Hardware
---

### Post by hyarmatey on 2012-08-03
First post after days of sifting through the forums and google results.
I had a rootkit on win7 and it owned that disk, so I got a friend to burn me a livecd and pulled the drive, formatted an alternate with ext4 (hybrid ssd 500Gb) and installed 12.04 32bit. It ran, but didn't shut down properly - I attributed that to the amd/ati switchable graphics and my troubleshooting thereof, but this issue I think is something else altogether.

Partitions were simple:
460 primary
40 swap

It booted and ran ok initially, but eventually  the uuid for swap got changed somehow and it couldn't mount it. blkid didn't report anything other than sda1 and when I eventually discovered gparted it showed:

/dev/sda1 - ext4 - 428Gb - boot
/dev/sda2 - extended - 37.35Gb - cannot modify via gparted
/dev/sda5 - unknown - 37.35gb - used to be swap

The first time through I reformatted the sda5 via gparted as swap, copied to uuid to assorted grub dealies, updated grub, but next boot it was gone again (new sda5 uuid not mountable that is). I then tried it via cmdline, with same result.

So, my simplest question amongst all the others I have is:
Where did this  extended partition come from? 

Given it matches swap in size, I was thinking crypswap, but I have not yet found reference to this in the myriad of Win/Ubuntu dual booters. That, and it's pretty greedy.

testdisk can't touch this extended partition either, although it does report detecting a dos partition first...
I welcome thoughts on the bootinfo results.txt attached.

Keep in mind the offending win7 rootkit drive was (similar hidden partitions was using a subprocess to repartition any connected drive - but this drive was removed - bios flashed with HP win+d on batteryless powerup updated bios bin - bios had been modified backwards by the remote owners). Prior to the bios reflash, anything that wasn't fat16/32 would become unbootable instantly.

Lots of questions, but one step at a time lest I confuse the issues.

Current bootinfo results from a liveusb (made from livecd ;-)

---

### Post by oldfred on 2012-08-03
When you installed you checked encrypt the /home folder. Then swap is also encrypted and gparted (or anything else) cannot see encrypted data.

The extended partition is one of the only 4 allowed primary partitions in the legacy MBR(msdos) partitioning scheme. It is the way to allow more than 4 by letting you create many logical partitions in the extended. Windows only boots from primary partitions, but LInux boots from logicals just fine.

Generally most desktops do not need a /boot unless old and have the 137GB boot limit or using server type RAID or LVM. Many still like smaller / (root) partitions and use a separate /home so you can easily reinstall system without having to backup all data in /home, but data should be backed up either way anyway.

But, I think what you called /boot is really just / (root) and contains the boot folder.

If only installing Ubuntu you may want to think about the newer gpt partitioning scheme. Not a lot of advantages, but all partitions are primary. Windows will not boot from gpt unless you have a new system that is UEFI.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

---

### Post by hyarmatey on 2012-08-03
Thanks OldFred.

Sorry for requesting clarification immediately, or perhaps I'm offering it, either way:

I remember seeing the grub info immediately after install, and it included the reference - 
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'

Since I had flattened and formatted the entire drive with ext4, and partitioned /@ 460 and /swap @ 40Gb (Basically 460 then what was left as swap - hybrid ssd has 40gb mem).

When I saw the part_msdos, the neck hairs went up, but new to Ubuntu I thought it may have seen a bios flag saying " windows 7" and done something nice for me a la compatibility rather then what I suspect actually happened. (Yes, I have evidence, but need a stable system to analyze/understand it)
ref: [http://www.eweek.com/c/a/Security/Black-Hat-Demonstrations-Shatter-Hardware-Hacking-Myths/](http://www.eweek.com/c/a/Security/Black-Hat-Demonstrations-Shatter-Hardware-Hacking-Myths/)

Di/re gressing, sorry - I understand the encrypted swap due to checking home directory encryption, but shouldn't that happen in assigned swap space like sda5? The extended partition was not my doing, nor was the /boot dir creation.  My investigations so far in the midst of instability have seen the win7 drives rootkit partitions reported as freedos in some tools.

So, second question (and I'm not averse to a second smackdown/rebuild in the end - but if I don't learn from it all I can, I lose):
Is there a reasonable circumstance for the installer to create this extended partion and add part_msdos in grubinfo when the entire drive was ext4?  Any hints why it *may* have been created by installer or OS afterwards?

I know full well that most folk claim BIOS viruses are black magic hokum, and I would have agreed - in the olden days. I don't know that I've even removed it as I've seen usb loading devices loading and calling video memory on boot when I had nothing jacked in. All speculation without understanding though. My bios was reverted, and I did find the payload, but my goal is a stable ubuntu system first. Paranoid - sure. Curious - even more so.

Thanks for the post and links.

---

### Post by oldfred on 2012-08-03
There are methods of partitioning a drive and formats for each partition on the drive.

The MBR(msdos) partitioning is the same as it has been since the first hard drive was added to the PC in the 1980's. Then it only had the 4 primary partitions and they soon realized users may want more and they then allowed one primary to become the extended partition. The extended is still a primary but is only a container for all the logicals. You do not directly use the extended.

MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

The newer partitioning scheme is gpt(GUID). I have gpt on two drives. You have to use gpt with drives over 2TB as back in the 1980s 2TB was not even considered, so MBR(msdos) had lots of room to grow. Windows will only boot with gpt with a new system using UEFI not BIOS to boot. Ubuntu can use gpt with BIOS or UEFI.
GPT Advantages srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by hyarmatey on 2012-08-03
Again, thanks for the links.
I shall absorb for awhile, but will post a picture for the word value.

My goal here is to understand (and thereby repair) whatever it was that "adjusted" the UUID and/or created the unusable block of 37Gb. I didn't do it, perhaps the Installer did, or the OS, but I don't know what default does in ubuntu 12.04 32bit when you specify only that "/" is 460GB ext4 and the rest is swap.  I would expect grub in the mbr and just ext4 after grubconf post install, no?

I know BIOS reads the MBR, but without knowing what to expect from ubuntu install, mine might be writing too.
If that's the case I have other, more elusive work to do, but no baseline to refer to.
Based on this photo - is this what one should expect from my setup? Encrypted swap lives in designated swap space right? It doesn't mean duplicate  - or does it?

---

### Post by hyarmatey on 2012-08-05
Since you were good enough to post some links, I thought I'd share what came out of it.
My brain turned to mush quickly embedding it into partitioning, mbr, and the like.

So, I tried the livecd again and went with defaults. This resulted in 40Gb of disk gone, in both gparted, and fdisk -l. I gathered some knowledge and tools, and did over.
This time, I used testdisk to write to the boot record and sniff partitions. Even testdisk didn't see everything that was missing, but once mbr was written to, the livecd partitioning tool could delete all partitions and reclaim that space. Go figger.

No "non boot disk" boot errors anymore either. I know they were writing mbr goodies, as I see registry references to \\?\..  (syntax from memory as it's offline and guarded by an attack rabbit).

I'm still looking for a tool to get at those hidden partitions on two old (from win7) drives with data on them.  They are not reported with blkid, fdisk, df. test disk sees "something", but sizes are off and it screams about cylinder, sector and head misreports. Fdisk shows:

```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7fbb36b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   625137344   312568641    7  HPFS/NTFS/exFAT

```Gparted shows some 22Gb missing. (2.5mb tailing unallocated)
Long way to go before you start sectoring... 32kbytes is a lot of room in assembly.

I'd love to get at it (boot record and missing partition) because I know there's some juicy data there.
I've read windows respects hidden flag on partitions, but linux sees recovery partitions easily.  Maybe I need to expand gparted's FS vocab to something more obtuse?

All kinds of goodies out there for windows, but I while the drive still boots fine, I don't own admin context anymore so results may vary.  I don't think this is a gparted bug, or installer flaw, but it's got me more curious than ever. 

Hints welcome.
cheers

---

### Post by oldfred on 2012-08-05
It looks like now you have one large NTFS partition.

Testdisk can find in many cases the old partitions that may contain data. But if it cannot find them then partitions are gone. Testdisk also offers photorec. I have used photorec to scan drive. But you must stop using drive as every write is overwriting some old data. Or make an image backup.

[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

All drives are now LBA.
Testdisk uses CHS - formula for conversion to LBA
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

Others:
gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

---

### Post by hyarmatey on 2012-08-06
Awesome links Oldfred.
Way to flatten my learning curve,

A couple related, referenced from yours:
Hirens Bootcd
[http://www.hiren.info/pages/bootcd](http://www.hiren.info/pages/bootcd)
Oddly, it wasn't linked there, but
[http://www.hirensbootcd.org/download/](http://www.hirensbootcd.org/download/)

The, the System Rescue CD
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

I had already started gathering lots of these bits for my little data quest, but like so many things - it's been done already. I was leaning toward a tweaked WinPE build...

I'm not sure how long to let this thread dangle, as my original problem has been resolved, although the cause was never established.  This will make someone's day when they find it.

---

