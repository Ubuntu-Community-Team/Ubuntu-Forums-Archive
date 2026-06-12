---
title: "Hard drive will not mount with manual options - exited with non-zero exit status 32"
date: 2017-03-26
forum: Hardware
---

### Post by TorturdChaos on 2017-03-26
I have 1 hard drive on my system that I cannot mess with the mount options.  Whether I edit fstab directly or use the Disk utility to setup the mount options manually so that the drive will auto mount on boot i get:
```
Error mounting system-managed device /dev/sde1: Command-line `mount "/home/chaos/Public/MediaShare/Software"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sde1,       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


 (udisks-error-quark, 0)



```

using these mount options: 
```
UUID=b3a15c0c-c05a-4989-badd-f5213ba2acba /home/chaos/Public/MediaShare/Software ext4 defaults,x-gvfs-show 0 2
```

which are the same that I use for all my other ext4 drives.

But if I leave the setting in the Disk Utilty "Automatic mount Options" On, the drive mounts just fine (I just can't auto mount it like that).  

I have tried fixing the drive with fsck:

```
sudo fsck /dev/sde1fsck from util-linux 2.20.1
e2fsck 1.42.9 (4-Feb-2014)
Software: clean, 11/61054976 files, 3883091/244190208 blocks
```

And it doesn't see anything wrong with it.

fdisk -l output for that device:
```
Disk /dev/sde: 1000.2 GB, 1000204886016 bytes255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004cda3


   Device Boot      Start         End      Blocks   Id  System
/dev/sde1            2048  1953523711   976760832   83  Linux
```



The drive is empty, and has bounced around between a few computers before ending up in my media server, so I tried reformating it.  No go.  Tired writing a new partition table to it with gparted, trying both msdos/mbr and gpt. Still didn't work.

There is a SATA expansion card in my system, but this drive is plugged directly into the mobo.

I have spent several afternoons on google trying to look up a solution to this but haven't found anything that works.  Anyone have an idea?

---

### Post by oldfred on 2017-03-27
Was drive ever RAID or LVM or Windows gpt converted to MBR, by Windows?
Those can leave meta-data on drive that interferes.

Are system expansion ports Asmedia?
Even plugging in a DVD to asmedia port can also cause drive issues.

---

### Post by TorturdChaos on 2017-04-14
Previously it was formatted to NTSF, but with standard MBR.

I'm not really sure about the [COLOR=#000000]Asmedia expansion ports.
Mobo on that machine is a [/COLOR]ASRock H97M Pro4 and there is a IOCrest SI-PEX40064 PCI-Express 2.0 Low Profile Ready SATA III (6.0 Gb/s) Controller Card for more SATA ports, but this particular HDD is plugged into a mobo SATA port.

---

### Post by oldfred on 2017-04-15
One user had a DVD plugged into Asmedia port and could not install.

---

