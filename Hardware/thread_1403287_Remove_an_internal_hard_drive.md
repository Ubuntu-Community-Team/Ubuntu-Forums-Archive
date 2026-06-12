---
title: "Remove an internal hard drive"
date: 2010-02-10
forum: Hardware
---

### Post by sonicnudge on 2010-02-10
In brief, I'd like to remove (and not replace!) an internal hard drive.

Although this sounds like it would be painfully easy, I have had no luck  in doing so, or finding an answer in many hours of Googling and reading  (and tinkering).

I am looking for a set of commands and/or files to modify to remove the  internal drive.

I am using a fresh install of 9.10 Server - i386/32 bit. (I am using the  default Grub2.)

FYI, the drive was originally mounted as /dev/sdf1. Formatted as XFS;  uses LVM(2). 

The most promising things I've tried:
 * Modified /etc/fstab, commenting out the drive
 * umount /dev/sdf1

Then:
1) Turn off machine, unplug drive.
2) Restart machine; invariably the boot hangs (immediately after  hardware initializations) at "GRUB Loading".

Other efforts:
 * Booted the Live CD, tinkered with System options (went into console;  tried chrooting in and performing update-grub with drive removed etc.)


Any feedback is appreciated!

Thanks in advance,
-Sonic

---

### Post by underquark on 2010-02-10
More information?
What other drives/partitions have you?
Where is root, home etc.
Are you removing a drive that is part of a RAID setup?

---

### Post by sonicnudge on 2010-02-10
Thanks for your quck replies!

Here is the output from df -hT:

```

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/mapper/fullback-root
              ext4     54G  1.8G   50G   4% /
udev         tmpfs    375M  200K  375M   1% /dev
none         tmpfs    375M     0  375M   0% /dev/shm
none         tmpfs    375M  280K  375M   1% /var/run
none         tmpfs    375M     0  375M   0% /var/lock
none         tmpfs    375M     0  375M   0% /lib/init/rw
/dev/sda5     ext2    228M   41M  176M  19% /boot
/dev/sdb1      xfs    280G  267G   13G  96% /media/media-01
/dev/sdc1      xfs    298G  288G   11G  97% /media/media-02
/dev/sdd1      xfs    298G  276G   23G  93% /media/media-03
/dev/sde1      xfs    298G  288G   11G  97% /media/media-04

```

This is probably a little overkill/redundant (given the above), but here is my /etc/fstab:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/mapper/fullback-root /               ext4    errors=remount-ro,usrjquota=aquota.user,grpjquota=aquota.group,jqfmt=vfsv0   0       1
# /boot was on /dev/sda5 during installation
UUID=2849129c-baf2-4281-a379-0614fdf62ba1 /boot           ext2    defaults        0       2
/dev/mapper/fullback-swap_1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0               udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0                            auto   rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /media/media-01                           xfs    defaults        0       0
/dev/sdc1       /media/media-02                           xfs    defaults        0       0
/dev/sdd1       /media/media-03                           xfs    defaults        0       0
/dev/sde1       /media/media-04                           xfs    defaults        0       0
# /dev/sdf1       /media/vault-01                           xfs    defaults        0       0

```

And finally (why not!?!), fdisk -l:

```

Disk /dev/sda: 61.5 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d183d18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7445    59801931   8e  Linux LVM
/dev/sda2            7446        7476      249007+   5  Extended
/dev/sda5            7446        7476      248976   83  Linux

Disk /dev/sdb: 300.1 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       36483   293049666   8e  Linux LVM

Disk /dev/sdc: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f0af544

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641   8e  Linux LVM

Disk /dev/sdd: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc7de01c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       38913   312568641   8e  Linux LVM

Disk /dev/sde: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae15f614

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       38913   312568641   8e  Linux LVM

Disk /dev/sdf: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       19929   160079661   8e  Linux LVM

```

(Here we see /dev/sdf[1], which had to be physically plugged in for Ubuntu to boot / to get this information.)


Please let me know if you are looking for different information.

Any and all feedback appreciated!

Thanks in advance,
-Sonic

---

### Post by sonicnudge on 2010-02-11
Feedback greatly appreciated!

Thanks,
-Sonic

---

### Post by sonicnudge on 2010-02-12
I'd like to remove (and not replace!) an internal hard drive in Ubuntu 9.10 server.

Anyone have a way to do this?

Thanks,
-Sonic

---

### Post by Claus7 on 2010-02-12
Hello,

back [then]("http://ubuntuforums.org/showthread.php?t=1154364&highlight=rest") I wanted to put one hdd at rest between two.

The thing is that you have to have grub installed in a machine that you do not won't to put at rest.

Find where grub is installed and then transfer it to another disk (which will remain in your system).

Hope it helped a little,
Regards!

---

### Post by sonicnudge on 2010-02-13
Claus7,

Thanks for the feedback!

I had already found and read your post, trying similar steps where applicable, but could make no progress. (Grub2 seems to handle these issues in a very different manner.)

In my case, Grub2 is installed on /dev/sda[5] (physical drive hd0). The drive I'd like to remove is /dev/sdf (physical drive hd5).

Any other thoughts? ALL feedback welcome!

Thanks in advance,
-Sonic

P.S.: I am beginning to think that there is no way to simply remove a physical drive in Ubuntu, short of a reinstallation of Ubuntu. (Wow. That would really suck. Could an OS be that short-sighted? I really don't believe this is the case with Linux/Ubuntu . . .)

---

### Post by sonicnudge on 2010-02-15
Note: This issue is not resolved. However, I figured that moving this post to "Server Platforms" might yield more positive results. Please see: [http://ubuntuforums.org/showthread.php?p=8830654](http://ubuntuforums.org/showthread.php?p=8830654)

-Sonic

---

### Post by Claus7 on 2010-02-16
Hello,

hope you find a solution. Sorry that I did not find out that you had grub 1.97. This is entirely new to me and many others I suppose. I really did not have my hands on this version, so I do not really know how it works. 

I had seen that it has a totally different structure than 0.97 grub from a cross post. The more people using it the more knowledge will be available to all.

Yet something more: if the new grub has a command line as the older version, it would be nice to post the commands you issued and the errors you encountered. That way, if the philosophy is the same, you might come closer to the solution you seek.

Glad if I was able to transfer even a small amount of aid.

Good luck,
Regards!

---

