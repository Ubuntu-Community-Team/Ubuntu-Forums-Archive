---
title: "jfs partitions won't mount on boot but will with 'sudo mount -a' once booted"
date: 2014-03-03
forum: Hardware
---

### Post by david169 on 2014-03-03
Hi, hopefully a very simple fix.

I've got a couple of jfs partitions which on boot is giving me the highly descriptive error:
'An error occured while mounting /media/Archive1.' 
'Press S to skip mounting or M for manual recovery'

if I hit M for manual recovery and the mount my fstab with 'sudo mount -a' it's all fine so is rather difficult to diagnose. 'dmesg | tail' or 'dmesg | grep jfs' doesn't even show anything so I have no idea where to even start looking for problems!

I've installed jfs utils and in gparted I've 'checked' the partitions several times which has fixed similar issues for me in the past.

I'm running XBMCBuntu, pretty much vanilla just updated my nvidia drivers. I had it working previously and not sure what I've done different this time around (I've reinstalled it a few times recently getting my GPU drivers working).

It would seem like it's trying to mount the filesystem without loading up the tools it needs to be able to mount it.

Is there any way I can move the mounting of fstab to the end of the boot process?

Thanks,
David

EDIT: jfs drives are defined in fstab by UUID

---

### Post by TheFu on 2014-03-03
Did you use **fsck**? 
A copy of the /etc/fstab would be helpful too.

---

### Post by david169 on 2014-03-03
Hi, thanks for the reply

yes, I've fsck.jfs on the drives... output from that is below

```

david@HTPC:~$ sudo blkid
[sudo] password for david:
/dev/sda1: LABEL="Archive1" UUID="da2909f9-e3f4-4a60-ba04-14564bf3a0ce" TYPE="jfs"
/dev/sdb1: LABEL="Archive2" UUID="5b57e085-d05b-4f62-a3d0-341f149838ef" TYPE="jfs"
/dev/sdc1: UUID="103b0dd3-ff47-4823-8e94-6228ea409127" TYPE="swap"
/dev/sdc2: UUID="c6d5caa1-6cb1-44a0-bdf3-4426bff6ee93" TYPE="ext4"
/dev/sdc3: UUID="18875501-8fd1-4e48-a3a1-270da95def21" TYPE="ext4"
/dev/sdd1: LABEL="UUI" UUID="3CD1-D920" TYPE="vfat"

```

```
david@HTPC:~$ sudo fsck.jfs /dev/sda1 -f
fsck.jfs version 1.1.15, 04-Mar-2011
processing started: 3/4/2014 0:14:58
The current device is:  /dev/sda1
Block size in bytes:  4096
Filesystem size in blocks:  488378368
**Phase 0 - Replay Journal Log
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Rebuild File/Directory Allocation Maps
**Phase 8 - Rebuild Disk Allocation Maps
1953513472 kilobytes total disk space.
     7802 kilobytes in 3293 directories.
1656508789 kilobytes in 15683 user files.
        0 kilobytes in extended attributes
   449749 kilobytes reserved for system use.
296562736 kilobytes are available for use.
Filesystem is clean.

```

```
david@HTPC:~$ sudo fsck.jfs /dev/sdb1 -f
fsck.jfs version 1.1.15, 04-Mar-2011
processing started: 3/4/2014 0:15:38
The current device is:  /dev/sdb1
Block size in bytes:  4096
Filesystem size in blocks:  488378368
**Phase 0 - Replay Journal Log
**Phase 1 - Check Blocks, Files/Directories, and  Directory Entries
**Phase 2 - Count links
**Phase 3 - Duplicate Block Rescan and Directory Connectedness
**Phase 4 - Report Problems
**Phase 5 - Check Connectivity
**Phase 6 - Perform Approved Corrections
**Phase 7 - Rebuild File/Directory Allocation Maps
**Phase 8 - Rebuild Disk Allocation Maps
1953513472 kilobytes total disk space.
     2239 kilobytes in 551 directories.
1822494820 kilobytes in 4016 user files.
        0 kilobytes in extended attributes
   437571 kilobytes reserved for system use.
130583320 kilobytes are available for use.
Filesystem is clean.

```

and my fstab is:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=c6d5caa1-6cb1-44a0-bdf3-4426bff6ee93 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=18875501-8fd1-4e48-a3a1-270da95def21 /home           ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=103b0dd3-ff47-4823-8e94-6228ea409127 none            swap    sw              0       0
UUID=da2909f9-e3f4-4a60-ba04-14564bf3a0ce    /media/Archive1    jfs
UUID=5b57e085-d05b-4f62-a3d0-341f149838ef    /media/Archive2    jfs

```

---

### Post by TheFu on 2014-03-03
The fstab is incorrect. It is missing 2 fields for the JFS mounts. These are NOT optional.

---

### Post by david169 on 2014-03-03
ok... looks like I've just managed to blag my way through using jfs for years then! I've changed it to the following and is all working well now - what's strange though is I've used the same lines of my fstab (literally copied and pasted) from my previous install that did work. Must have been a fluke.

Anyway thanks for the heads up,
Dave

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=c6d5caa1-6cb1-44a0-bdf3-4426bff6ee93 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sdc3 during installation
UUID=18875501-8fd1-4e48-a3a1-270da95def21 /home           ext4    defaults        0       2
# swap was on /dev/sdc1 during installation
UUID=103b0dd3-ff47-4823-8e94-6228ea409127 none            swap    sw              0       0
UUID=da2909f9-e3f4-4a60-ba04-14564bf3a0ce	/media/Archive1	jfs	defaults	0	2
UUID=5b57e085-d05b-4f62-a3d0-341f149838ef	/media/Archive2	jfs	defaults	0	2



```

---

