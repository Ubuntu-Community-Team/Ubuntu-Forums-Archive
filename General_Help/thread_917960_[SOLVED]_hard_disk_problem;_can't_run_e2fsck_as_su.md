---
title: "[SOLVED] hard disk problem; can't run e2fsck as suggested"
date: 2008-09-12
forum: General Help
---

### Post by danzinho on 2008-09-12
Hi

For no obvious reason, after a reboot yesterday my second disk appears to be corrupted.  I get this in /var/log/fsck/checkfs

Log of fsck -C3 -R -A -a 
Fri Sep 12 17:39:31 2008

fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sdb1
/dev/sdb1: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8


Naturally, 'sudo e2fsck -b 8193 /dev/sdb1' is the first thing I try, but I get 

e2fsck 1.40.8 (13-Mar-2008)
e2fsck: Device or resource busy while trying to open /dev/sdb1
Filesystem mounted or opened exclusively by another program?

It doesn't actually appear to be mounted (according to umount) and fuser doesn't find any processes that are tying it up.

How can I proceed?

Incidentally, 'mak2fs -n /dev/sdb1' gives me different numbers to try, but I get the same message as above.

The program 'testdisk' (other threads) seems to see the second disk OK.

I'll append my 'fdisk -l' and 'cat /etc/fstab' output in case it helps

Many thanks!
-------------------------------------------------------------------------
daniel@thymine:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       87508   702907978+  83  Linux
/dev/sda2           87509       91201    29664022+   5  Extended
/dev/sda5           87509       91201    29663991   82  Linux swap / Solaris

Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72288b81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732571648    7  HPFS/NTFS

-------------------------------------------------------------------------
daniel@thymine:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d3da5b5-a84e-4f75-bbee-5eb6899c3600 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5216b8a3-36b8-4ab9-bc63-843fe348af49 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/hdb1
/dev/sdb1  /disk2	ext3	defaults	0	2

---

### Post by HalPomeranz on 2008-09-12
It sounds like you're doing the right thing:

1) Use "mkfs -n /dev/sdb1" to get a list of alternate superblocks

2) Use "fsck -b" with alternate superblock numbers to try and recover your file system

The one thing I do notice about the fdisk output you posted is that the file system in /dev/sdb1 is marked as NTFS in the output of fdisk.  I'm not sure if that's confusing fsck or not.  You could use fdisk to relabel the file system as a "Linux" type file system and see if that makes a difference.  Be careful to only change the file system label, and not the partition geometry!

---

### Post by Herman on 2008-09-12
> The one thing I do notice about the fdisk output you posted is that the file system in /dev/sdb1 is marked as NTFS in the output of fdisk. I'm not sure if that's confusing fsck or not.Yes, I agree with HalPomeranz, 

```
daniel@thymine:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe0000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       87508   702907978+  83  Linux
/dev/sda2           87509       91201    29664022+   5  Extended
/dev/sda5           87509       91201    29663991   82  Linux swap / Solaris

[B]Disk /dev/sdb: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72288b81

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       91202   732571648    7  [COLOR=Red]HPFS/NTFS[/COLOR][/B] 
```:) That's really strange, your fdisk output indicates that your /dev/sdb1 partition contains an NTFS file system, but it's registered in your /etc/fstab file as ext3.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=0d3da5b5-a84e-4f75-bbee-5eb6899c3600 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5216b8a3-36b8-4ab9-bc63-843fe348af49 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
[B]# /dev/hdb1
/dev/sdb1  /disk2    [COLOR=Red]ext3[/COLOR]    defaults    0    2[/B]
```Is there any possibility that you or someone else with access to your computer might have (accidentally or on purpose) reformatted that partition from ext3 to NTFS? (Without updating /etc/fstab?) :)

If the partition really does contain an NTFS file system then you should edit /etc/fstab so the operating system will know it's NTFS and treat the file system accordingly. You would put a '0', (zero) in both the 'dump' and 'pass' columns in /etc/fstab, to make Linux skip the file system check, since Linux doesn't check NTFS at all anyway.
If the partition really is ext3, then I'm not sure what you'll have to do...
... After pausing to think, I agree with HalPomeranz again, if we assume that maybe your partition table has the wrong information, (I don't know how that could happen, but fdisk reads the partition table). 
 > You could use fdisk to relabel the file system as a "Linux" type file system and see if that makes a difference. Be careful to only change the file system label, and not the partition geometry!Yes, that should work or else use TestDisk. TestDisk reads the file system blocks and writes a new partition table according to what partitions and file systems it finds are actually there. 

:oops:  I feel a little silly for repeating what another poster has already said, but more people might be able to understand better if it's explained more, so I'll just leave it like this...

---

### Post by danzinho on 2008-09-15
Dear both

Thanks very much for your help.  You put your finger right on the problem - the mismatch between the NTFS reported by fdisk and the ext3 in my /etc/fstab.  When I change the /etc/fstab line to

/dev/sdb1  /disk2	ntfs	defaults	0	0

everything seems to be fine - my content is there and readable.

This situation arose because the machine came pre-installed with Windows (ntfs).  When I installed Ubuntu, it didn't touch the second disk.  In my ignorance, when I came to mount /disk2 and add the line to /etc/fstab, I assumed the disk was ext3.

Now there is a small follow-up question

Should I try to change disk2 to the ext3 format?  Are there any significant advantages to ext3 (disk checking perhaps) or issues with ntfs support?  Older threads suggest that ntfs support is imperfect, but perhaps that is resolved by now.

Many thanks again

Daniel

---

### Post by Herman on 2008-09-15
Well, there's no hurry. Not so long ago we needed an extra FAT32 partition to share data between Windows and Linux. Linux NTFS support is very good these days, we can read and write to an NTFS file system quite safely now.  
We still can't run a proper file system check in an NTFS partition though, (at least not the last time I checked), ntfsprogs contains ntfsfix, but according to the documentation all that does is mark the file system as 'dirty', so Windows will run CHKDSK on iit automatically next time someone boots Windows.

If you're only using Linux, and you have no Windows now at all, (good), you might eventually change it to ext3. The ext3 file system is in my opinion more robust and if anything does go wrong it's the easiest to repair. 

I had a whole hard disk formatted with NTFS for a long time, (just for something different), and kept all my data in it, and I had no problems. I have no Windows in this computer, I just wanted to try NTFS out, that's all. Nothing went wrong with it, but I got tired of it and formatted it back to ext3 eventually. :)

---

### Post by illpig on 2008-10-03
i have the same problem like the post-starter. but here its not with ntfs.

```
 sudo fdisk -l

Platte /dev/sda: 33.8 GByte, 33820286976 Byte
255 Köpfe, 63 Sektoren/Spuren, 4111 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1       30401   244196001   83  Linux

```

so you see, its set as linux but there is "device or resource busy" while trying to restore the superblock with:

```
 sudo e2fsck -b 32768 /dev/sda
e2fsck 1.41.0 (10-Jul-2008)
e2fsck: Device or resource busy beim Versuch, /dev/sda zu öffnen
Ist das Dateisystem eingehängt or exklusiv von einem anderen Programm geöffnet worden?

``` 

 what to do?

thanks illpig

---

### Post by Herman on 2008-10-03
:D
I think you just have an error in your command,
```
sudo e2fsck -b 32768 /dev/sda
```See where you have '/dev/sda' there? Your computer will think you're trying to run a file system check in your MBR.
You must specify a partition number because you can't have any file system in your MBR, it must be in a partition,
```
sudo e2fsck -b 32768 /dev/sda**1**
```Regards, Herman :)

---

### Post by illpig on 2008-10-03
thx! this and using ver. 1.41.2, that solved the problem!

cheers illpig

---

