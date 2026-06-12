---
title: "Finding the MBR?"
date: 2009-10-20
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-10-20
from this fdisk report can anyone tell me where my mbr lies?? I have no idea how to read this. i'm guessing maybe sda2 because of the (lba) label. Thanks for your help----my next step is to back it up...


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10308    72565602    e  W95 FAT16 (LBA)
/dev/sda3           10309       19457    73489342+   5  Extended
/dev/sda5           10309       13496    25606810    7  HPFS/NTFS
/dev/sda6           17459       19457    16056936    7  HPFS/NTFS
/dev/sda7           13497       13739     1951866   82  Linux swap / Solaris
/dev/sda8           13740       14590     6835626   83  Linux
/dev/sda9           14591       15563     7815591   83  Linux

---

### Post by toolmanpaul on 2009-10-20
then i backup 512 bytes of that partition ...i think??

---

### Post by wilee-nilee on 2009-10-20
You might want to share what your trying to do, so that if your taking the longest distance to a fix that is done in a much easier way can be implemented.

---

### Post by oldfred on 2009-10-21
The MBR is not part of any partition.

[http://en.wikipedia.org/wiki/Boot_sector](http://en.wikipedia.org/wiki/Boot_sector)

---

### Post by mcduck on 2009-10-21
> **toolmanpaul said:**
> from this fdisk report can anyone tell me where my mbr lies?? I have no idea how to read this. i'm guessing maybe sda2 because of the (lba) label. Thanks for your help----my next step is to back it up...


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1274    10233373+  12  Compaq diagnostics
/dev/sda2   *        1275       10308    72565602    e  W95 FAT16 (LBA)
/dev/sda3           10309       19457    73489342+   5  Extended
/dev/sda5           10309       13496    25606810    7  HPFS/NTFS
/dev/sda6           17459       19457    16056936    7  HPFS/NTFS
/dev/sda7           13497       13739     1951866   82  Linux swap / Solaris
/dev/sda8           13740       14590     6835626   83  Linux
/dev/sda9           14591       15563     7815591   83  Linux

The MBR is *always* at the very beginning of the disk, before any partitions.

---

### Post by Herman on 2009-10-21
:) Here's a link that should help, [MBR backup and restore]("http://members.iinet.net.au/%7Eherman546/p13.html#mbr_dd").

There is a MBR at the start of the first hard disk, and there is also one in the first sector, (sector 0), of any more formatted hard disks you might have plugged into your computer. 
Usually only the first hard disk will be the one your BIOS will boot unless you do something to cause it to do otherwise.

The MBR of the first hard disk is usually specified as /dev/sda in the dd command.
If we want to copy a partition boot sector instead we type something like /dev/sda1 or /dev/sda2 or whatever the partition number is.
If we type /dev/sdb, that would give us the MBR of the second hard disk.

Unless you know what you're doing and have a special reason for doing so, it's generally not a good idea to make a backup of the MBR which includes all 512 bytes because that would include the partition table. The danger is if you change your partitions and then restore the MBR backup containing a not out of date version of the partition table you would lose access to some or all of your partitions and data.
If you only make a backup of the first 446 bytes you'll have the boot loader code and the MBR disk identifier. That should be sufficient for most purposes.

Actually, the boot loader code for most boot loaders can easily be written to the MBR using programs like grub-install or for Windows XP, fixmbr.

A backup of the MBR which includes the disk identifying number is useful to Windows users if they need to clone Windows Vista or Windows 7 to a new hard disk, for example if they have a hard disk that's failing. For some reason Windows is designed not to boot if it detects the fact that it has been cloned to a new hard disk. I don't know what the benefit is of that is supposed to be for Windows users, but it's good for Linux. :)

---

### Post by Herman on 2009-10-21
> The MBR is not part of any partition.:) That's right, I agree with oldfred.
> The MBR is *always* at the very beginning of the disk, before any partitions.I agree with mcduck too.

If you want to see what sector numbers you partitions start and finish in, you can use the fdisk command with the -lu options instead of only -l, like this,
```
sudo fdisk -lu
```The result of that command will show that the first partition almost always begins in sector 63, except in the case of Vista and Windows 7, which normally don't begin until sector 2048.
The MBR is in sector 0, so that means there are either 63 empty sectors after the MBR or 2048 sectors after the MBR that aren't part of any partition at all so they don't belong to any particular operating system and are not used for storing any regular files.
Some boot loaders like GNU GRUB and GAG Boot Manager use that spare area for storing extra boot loader code.

---

### Post by Herman on 2009-10-21
:) If it's the partition table part of the MBR that you're worried about, there's an excellent program called TestDisk available to Linux users which is useful for reconstructing the partition table as well as quite a few other important tasks, [COLOR=#C0C0C0][/COLOR][TestDisk - CG Security]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by toolmanpaul on 2009-10-21
> **wilee-nilee said:**
> You might want to share what your trying to do, so that if your taking the longest distance to a fix that is done in a much easier way can be implemented.

practicing safe-computing...read that a backup of the mbr might save me some grief down the road. i have in the past had computers quit working. i just like to learn how things work.! i puts allot with my computers...

---

### Post by Herman on 2009-10-21
> practicing safe-computing...read that a backup of the mbr might save me some grief down the road.:) Yes, good idea.

One of the reasons why many people feel the MBR is a scary subject is because we can't normally 'see' the MBR or the changes we make to it.
```
sudo dd if=/dev/sda count=1 | hexdump -C
```If you want to see what your MBR looks like in hexadecimal code, you can use the above command to take a look at it. 

Here's a link that might interest you, [What does a MBR really look like?]("http://members.iinet.net.au/%7Eherman546/p6.html#What_does_an_IPL_really_look_like")

If you have more than one hard disk in your computer, you can try copying the output from the above command to an empty text file and save it as 'file1'.
Then if you want to you might repeat the same command but replace '/dev/sda', with '/dev/sdb', to get the hex representation of your second hard disk's MBR. 
If you copy that to a file and name it 'file2', you can compare the differences with 'Meld Diff Viewer', which is a really cool program for comparing two files and highlighting the differences between them.
Meld Diff Viewer can be installed by searching for it in 'Applications'-->'Add/Remove Programs', or by using 'System'-->'Administration'-->'Synaptic Package Manager', or by using a command like 'sudo apt-get install meld'.

If you don't have any other hard disks, you might want to wait until you need to make some changes to your partitions or boot loader to take a look at your MBR before and after to see what changes you made.

If you have an old hard disk you don't have vital information in or even better, an older computer you can play with you can safely experiment with the MBR without risking any inconvenience to yourself, (bv temporarily losing accessing your data).
You can try installing different boot loaders and comparing the MBR before and after to learn what has been changed.

Once you can 'see' what's happening in the MBR when we use commands to change boot loaders or make changes to the partition table, you'll feel much more confident and in control. :)

---

### Post by wilee-nilee on 2009-10-21
Looking at the post count and the question it seemed appropriate to get more information then just to dispense instructions.

---

### Post by toolmanpaul on 2009-10-21
> **Herman said:**
> :) That's right, I agree with oldfred.
I agree with mcduck too.

If you want to see what sector numbers you partitions start and finish in, you can use the fdisk command with the -lu options instead of only -l, like this,
```
sudo fdisk -lu
```The result of that command will show that the first partition almost always begins in sector 63, except in the case of Vista and Windows 7, which normally don't begin until sector 2048.
The MBR is in sector 0, so that means there are either 63 empty sectors after the MBR or 2048 sectors after the MBR that aren't part of any partition at all so they don't belong to any particular operating system and are not used for storing any regular files.
Some boot loaders like GNU GRUB and GAG Boot Manager use that spare area for storing extra boot loader code.

fdisk -lu reveals this....but i'm still not shure if the mbr will be in sda1 or sda2 ?.. Duel booting with windows vista installed first on an acer laptop...if this helps ?

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x7e8890fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20466816   165598019    72565602    e  W95 FAT16 (LBA)
/dev/sda3       165598020   312576704    73489342+   5  Extended
/dev/sda5       165598088   216811707    25606810    7  HPFS/NTFS
/dev/sda6       280462833   312576704    16056936    7  HPFS/NTFS
/dev/sda7       216813303   220717034     1951866   82  Linux swap / Solaris
/dev/sda8       220717098   234388349     6835626   83  Linux
/dev/sda9       234388413   250019594     7815591   83  Linux

---

### Post by oldfred on 2009-10-22
The computer BIOS boots the first hard drive in the system, usually sda but sometimes bios, grub and linux do not agree and first drive. The MBR is just on a drive.

The * says that the partition is flagged as the boot partition. Only required by windows so that is usually the first windows partition and the one that is booted. Since your sda1 is a compaq partition it has diagontics and perhaps the original windows install disk.

If you have Vista I am surprised that it is installed in FAT16! It should be in NTFS partition. Or do you still have an old win95 and added vista?

---

### Post by Herman on 2009-10-22
/dev/sda is the hard disk which contains partitions /dev/sda1, /dev/sda2 and the others.
 Your MBR is in sector 0 of /dev/sda, which is the first sector of the hard disk.
The letters MBR stand for Master Boot Record, because there is only one of those for each hard disk. The MBR has space in it reserved for boot loader code so it might also be called a 'boot sector', but it's a special kind of boot sector.  The MBR also contains the partition table. Without the Master Boot Record we couldn't have any partitions. Therefore it's called the Master Boot Record.

/dev/sda1 and /dev/sda2 are partitions.
Sector number 63 of /dev/sda is where your first partition, /dev/sda1, begins.
Sector number 20466816 is the starting sector of your number 2 partition.
The first sector of a partition sometimes contains code for a boot loader too, and so it may be called a 'boot sector', or 'partition boot sector', because it's located in a partition.
There can be many partitions in a hard disk and they all have a space in their first sector for bootloader code. A partition boot sector is just another boot sector, boot sectors are not as important as the MBR. 

Most linux operating systems have an empty boot sector by default and easily boot up right from the MBR, which points directly to the boot loader inside the Linux partition.
With Windows things are different, the boot is always relayed from the MBR, through the boot sector and then to the boot loader. If there's no boot code in the MBR then the primary partition marked 'active', (with the boot flag in the partition table) will be booted. For Windows, the boot sector is as vital as the MBR.

There are still a lot of web site authors who use the terms 'Master Boot Record' and 'boot sector' interchangeably, so it's no wonder a lot of people are still confused.
It can be a problem if people mistakenly think /dev/sda1 is their MBR and try to install GRUB there because if /dev/sda1 happens to be a Windows partition as it most often is, that will cause Windows to become unbootable until the problem is fixed, which can be very inconvenient for the computer's owner. That's why it's important to try agree on the definition of computer terms and to try to be consistent in the way we apply them.
It's a good thing that you're asking these questions because it might help clear things up for other people too. This is how I think these terms should be used anyway.

---

### Post by toolmanpaul on 2009-10-22
> **oldfred said:**
> The computer BIOS boots the first hard drive in the system, usually sda but sometimes bios, grub and linux do not agree and first drive. The MBR is just on a drive.
 
The * says that the partition is flagged as the boot partition. Only required by windows so that is usually the first windows partition and the one that is booted. Since your sda1 is a compaq partition it has diagontics and perhaps the original windows install disk.
 
If you have Vista I am surprised that it is installed in FAT16! It should be in NTFS partition. Or do you still have an old win95 and added vista?
 
Bought new with  vista, all i did was install xubuntu from downloaded iso... i like x but wi-fi does not work  ,,   that's a new thread...

---

### Post by toolmanpaul on 2009-10-22
HERMAN...u gave alot of info...thanks....i'll have to read some of your links and hope it becomes clear....i don't like doing damage while trying to manage damage-control....

---

