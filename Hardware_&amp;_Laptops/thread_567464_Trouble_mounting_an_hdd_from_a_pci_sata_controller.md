---
title: "Trouble mounting an hdd from a pci sata controller"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by Lonergan on 2007-10-04
My problem: SATA drive won't mount at all.

One 500 GB SATA drive with one single NTFS partition connected to a SIIG SATA II-150 PCI card.  If I sudo fdisk -l
I see this:

```
Disk /dev/sde: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       60801   488384001    7  HPFS/NTFS

```

This is correct.  This drive is 100% working and useable in under Windows XP.

If I go to System-->Preferences-->Hardware Information, I see that my drive is connected to

INI-1623 PCI Sata-II Controller and this is using the sata_inic162x driver.

Even though this is a SIIG card it seems to be using the Initio chip which is fine.  Looking at the information in the driver text file for the Windows install, it is indeed using Initio 1623.  So far so good, it seems Ubuntu is seeing and installing the correct driver.

So why won't it automount like my other SATA drives?  The other 4 use the onboard Nvidia controller on my motherboard (sata_nv) so they are distinct and have no problems.  Of those 4 drives 3 are NTFS and have ntfs-3g running and working perfectly.

If I then try to mount as root:

mount /dev/sde1 /media/iTunes for instance....I get nothing.  Or rather, it mounts but not correctly.  I can't get to the drive as normal user but as root I can cd to it.  If I issue an ls -l command I get an input/ouput error:

```
zanth@SolaceII:~$ cd /media/iTunes
bash: cd: /media/iTunes: Permission denied
zanth@SolaceII:~$ sudo -s
root@SolaceII:~# cd /media/iTunes
root@SolaceII:/media/iTunes# ls
ls: reading directory .: Input/output error
root@SolaceII:/media/iTunes# ls -las
ls: reading directory .: Input/output error
total 0
```




Going to My Computer /media I see that /media/iTunes is locked and that the .hal-mtab-lock is present.

I'm at a loss as to what is the problem.  Any help would be very much appreciated even if that help comes in the form of a suggestion for a known working SATA controller from some other company.

Thanks

---

### Post by dabl on 2007-10-04
Couple of notions (not solutions, yet):

-- what does dmesg say about the bootup process, vis a vis that drive on the PCI bus?

-- Does it have a UUID assigned?  What does ```
blkid
``` show for it?

I'm thinking if you could eliminate the possibility that there is some sort of contention on the PCI bus, due to the 2 SATA controllers, then you could focus on the possibility of "mount by UUID" using a special /etc/fstab line, which would look similar to this one:

```
# /dev/sde1
UUID=d182b7c3-298c-49b3-ac66-b378033b815c /media/sde1 ntfs-3g nouser,defaults,noatime,auto,rw,dev,exec,suid 0 2
```

:)

---

### Post by Lonergan on 2007-10-04
Interesting, dabl.  Not only does my motherboard have 4 SATA connectors it also has a raid controller which is SIIG 3114 compatible I believe, it uses the sata_sli driver anyway.

In another thread I read up on before creating this thread, I did note a guy who had major issues with his SATA drives (10 I think) which would, on reboot, change SATA id, so that sata 1 could end up being dev/sdb instead of sda and then the next time sdc and back to sda, so that fstab was useless.  This has happened to me a few times where my /dev/sde drive will mount as sda even though this should be my ubuntu hd (linux is on its own drive so that all three necessary partitions are usually sda1,2 3.

Maybe then the driver is okay but there is a conflict like you suggest.

Here is my blikid output:

```
/dev/sda1: UUID="40d13703-3368-417d-b54b-6f250b9c6419" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: TYPE="ntfs" 
/dev/sdc1: TYPE="ntfs" 
/dev/sdd1: TYPE="ntfs" 
/dev/sde1: TYPE="ntfs" 
/dev/sdd2: TYPE="ntfs" 
/dev/sda2: UUID="5716274a-e2e0-4749-ad89-b249128493e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="0d202b82-99af-4a85-9bb0-4c1743285b63" TYPE="swap" 
```


And here is some info from dmesg:

```
[ 6669.172000] NTFS-fs error (device sde1): ntfs_readdir(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6674.332000] NTFS-fs error (device sde1): ntfs_readdir(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup_inode_by_name(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup(): ntfs_lookup_ino_by_name() failed with error code 5.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup_inode_by_name(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup(): ntfs_lookup_ino_by_name() failed with error code 5.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup_inode_by_name(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup(): ntfs_lookup_ino_by_name() failed with error code 5.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup_inode_by_name(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup(): ntfs_lookup_ino_by_name() failed with error code 5.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup_inode_by_name(): Directory index record with vcn 0x0 is corrupt.  Corrupt inode 0x5.  Run chkdsk.
[ 6764.676000] NTFS-fs error (device sde1): ntfs_lookup(): ntfs_lookup_ino_by_name() failed with error code 5.
```

Now that is very interesting.

If there is anything I missed here is the entire dmesg:  [http://paste-it.net/3826](http://paste-it.net/3826)

seems the proper drivers were mounted for it.

---

### Post by Lonergan on 2007-10-04
I rebooted, ran chkdsk and dmesg no longer shows the error messages but I still can't mount the disk.

some further information to help out maybe:

card is located on pci bus 5 device 6 irq 16 in windows
it is an initio inic1620 s-ata card (ven_1101, dev_1622)

oddly though...also appaering on pci bus 5 though device 10 and irq 19 is a sil3114 rev. 2 which is a raid device. 

My motherboard is an Asus ASN-A8N-SLI Premium mps 1.4, 4 sata connectors on board which are all usd and 4 sata raid connectors, none used and apparently they use the sil 3114 driver.

---

