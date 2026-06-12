---
title: "bizzare sudden change in hard drive behavior"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by jsgarvin on 2007-08-14
I've got two SCSI hard drives on my desktop running Feisty.  For the last year or so, right up until this morning, they were /dev/sda and /dev/sdb.  As of this morning, they've spontaneously decided to become /dev/sdc and /dev/sdd.  It appears that the only thing allowing my machine to boot at all is that the /etc/fstab refers to certain critical partitions via a UUID rather that directly to /dev/sda.  But every boot is giving me errors because it's trying to do an filesystem check on sda and sdb and not finding them.  Below is what I think is the most useful info.  I'd much appreciate it if someone had some insight into what the hell happened, why, and how I can avoid it in the future.  Thanks.  I could certainly just change my fstab to point to sdc and sdd, but I think that would be treating the symptom, not the sickness.
Note: /dev/sdb was recently reformatted and mounted as /mnt/betty, so I'm suspecting that may have something to do with this, I just don't know what.

**/etc/fstab**
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7bab3faf-ed63-460a-b682-5be70b6ef705 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda9
UUID=0ce61892-79c3-4884-ad24-73bbc5e91527 /home           ext3    defaults        0       2
# /dev/sda6
UUID=0aba0dd8-9dcc-4224-bd41-634d2a7a4b14 /tmp            ext3    defaults        0       2
# /dev/sda8
UUID=dd8eb291-b970-44da-af15-544cc5987a29 /usr            ext3    defaults        0       2
# /dev/sda7
UUID=d25c40c4-c82e-4524-9410-aaa43818dcbb /var            ext3    defaults        0       2
# /dev/sda5
UUID=74a7df5f-7cee-49a8-be85-8d0827b3995a none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda3       /mnt/bigun      ext3    defaults        0       2
/dev/sdb1       /mnt/betty      ext3    defaults        0       2
```

**df**
```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdc2              8309452    472168   7415180   6% /
varrun                 1647528       200   1647328   1% /var/run
varlock                1647528         0   1647528   0% /var/lock
procbususb             1647528       132   1647396   1% /proc/bus/usb
udev                   1647528       132   1647396   1% /dev
devshm                 1647528         0   1647528   0% /dev/shm
lrm                    1647528     33788   1613740   3% /lib/modules/2.6.20-16-generic/volatile
/dev/sdc9             20327176  11671040   7623560  61% /home
/dev/sdc6              2229516     68996   2047264   4% /tmp
/dev/sdc8             16231544   2889072  12517940  19% /usr
/dev/sdc7              4119172   1812556   2097372  47% /var
```

**/var/log/fsck/checkfs**
```
Log of fsck -C -R -A -a
Tue Aug 14 08:19:49 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/sda3^M
/dev/sda3:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/sdb1^M
/dev/sdb1:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/sdc9: clean, 95666/2583616 files, 2998845/5162881 blocks
/dev/sdc6: clean, 24/283392 files, 26148/566283 blocks
/dev/sdc8: clean, 129931/2064384 files, 787054/4122672 blocks
/dev/sdc7: clean, 22492/523264 files, 469567/1046225 blocks
fsck died with exit status 8

Tue Aug 14 08:19:49 2007
----------------
```

---

### Post by jsgarvin on 2007-08-14
bump

---

### Post by elektronaut on 2007-08-14
fsck is saying it can't find neither /dev/sda3^M nor /dev/sdb1^M. I have no idea why the strings are not correct, but as far as I know you should only work with UUID's in fstab since Feisty. Try the command 'blkid' or 'sudo ls -la /dev/by-uuid' to get the UUID's for sda3 and sdb1 and replace the entries in fstab in the same way like the first ones.

---

### Post by jsgarvin on 2007-08-14
Well, equally strange, after multiple reboots this morning with both trying to be sdc and sdd, this evening when I fired it up, they went right to sda and sdb.  However, thanks for the info, I'll make changes to the fstab to use UUIDs instead.  And I'll add some comments to the fstab so that next time I know how to do it again.

---

