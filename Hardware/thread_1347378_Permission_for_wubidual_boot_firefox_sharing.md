---
title: "Permission for wubi/dual boot firefox sharing"
date: 2009-12-06
forum: Hardware
---

### Post by Boulemans on 2009-12-06
I've upgraded my wubi system from 9.04 to 9.10. The set-up for my laptop is: 
VistaDisk, NTSF (where vista is installed); 
WubiDisk, NTSF (where wubi is installed); 
DualDisk, FAT32 (for document sharing and Firefox profile sync)

My fstab conf. file looked like this under 9.04 (copy-pasted from a website into the fstab)

```
/dev/sda1 /media/VistaDisk ntfs-3g defaults,locale=nl_BE.UTF-8 0 0
/dev/sda4 /media/FileDisk ntfs-3g defaults,locale=nl_BE.UTF-8 0 0
/dev/sda7 /media/DualDisk vfat defaults,umask=007,gid=46 0 0
```

This worked under 9.04. However, since 9.10 my DualDisk is mounted at /media/DualDisk, but named "18 GB filesystem" at the desktop (odd, but not dramatic). 

A more serious change is the fact dat Firefox can't delete the .parentlock file in the shared profile at the DualDisk partition. I searched the web and thought it must be the permission arrangements for the disk. When searching the web for mor info (man mount, man fstab), I realised that my gid is 1000, not 46, so I changed that. The problem wasn't solved. Firefox seems to be able to delete the .parentlock files when I changed the code to:

```
/dev/sda7 /media/DualDisk vfat defaults,dmask=001,fmask=001,uid=1000,gid=1000 0 0
```

Although I thinc I give myself gigantic permission to the partition, this did NOT solved the problem. Firefox still can't delete the .parentlock file. Manually i get the error that it is a Read-only filesystem.

---

### Post by Boulemans on 2009-12-06
FIrst of, is this the right forum for this topic? if not, how do I change this to "General Help" or something?

In various post i've seen that this can be important additional information:

```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             12G  7.4G  3.4G  69% /
udev                  941M  276K  940M   1% /dev
none                  941M  420K  940M   1% /dev/shm
none                  941M   92K  941M   1% /var/run
none                  941M     0  941M   0% /var/lock
none                  941M     0  941M   0% /lib/init/rw
/dev/sda6              22G   13G  8.8G  60% /host
/dev/sda1              25G   20G  5.7G  78% /media/VistaDisk
/dev/sda4             8.2G  5.3G  2.9G  65% /media/FileDisk
/dev/sda7              18G   13G  5.1G  72% /media/DualDisk
/dev/sdb              2.0G  8.5M  1.9G   1% /media/F891-21DF

```

and ```
fdisk -l
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x43ad9a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3235    25985106    7  HPFS/NTFS
/dev/sda3            3366        8670    42612412+   5  Extended
/dev/sda4            8671        9729     8506417+   7  HPFS/NTFS
/dev/sda5            8546        8670     1004062+  82  Linux swap / Solaris
/dev/sda6            3366        6136    22257994+   7  HPFS/NTFS
/dev/sda7            6271        8545    18273906    b  W95 FAT32

Partition table entries are not in disk order

Disk /dev/sdb: 2041 MB, 2041012736 bytes
63 heads, 62 sectors/track, 1020 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      199216      491461   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(199215, 34, 11)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(491460, 44, 51)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?       43188      538843   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(43187, 17, 47)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(538842, 14, 42)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      478721      974376   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(478720, 18, 30)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(974375, 14, 39)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           1      931190  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(931189, 36, 30)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order

```

---

### Post by oldfred on 2009-12-06
I do not use Wubi, but have full dual boot install (actually 4 versions) and up untill last month had firefox and thunderbird on Fat share partition. I just converted to NTFS. These entries have worked for me.

# Entry for /dev/sda4 :
UUID=46CD-C9B2                             /home/fred/share   vfat         user,auto,fmask=0111,dmask=0000      0  0  

# Entry for /dev/sdc2 :
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults                             0  0  

In 9.10 I made some changes to the NTFS and have not tried the FAT
UUID=44332FD360AA9657                      /home/fred/shared  ntfs-3g      defaults,rw,noexec,nosuid,locale=en_US.UTF-8,fmask=0111,dmask=0000          0  0  

All the text files came up executable, so I added noexec and some other setting which I think are duplicate of default standard.

---

### Post by Boulemans on 2009-12-07
After trying the possibility of oldFred, nothing changed. The partition was mounted, but still as "read-only filesystem". should I report this as a 9.10 bug? i didn't have this problem with 9.04.

EDIT: I changed the partition to NTSF, and since then i had no permission problems. Though I just evaded the problem, this is 'solved' for me :-)

---

