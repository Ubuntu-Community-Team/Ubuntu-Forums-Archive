---
title: "Invalid node structure after using DD command"
date: 2018-08-20
forum: Hardware
---

### Post by cskambis on 2018-08-20
Hey there,

First time poster. I have a WD 2 TB drive that I tried to clone onto another HDD, a similar WD 2 TB drive. When I used the dd command to do so, and once the command finished executing, the cloned drive could not mount and I got the following error: 

```
Error mounting /dev/sdb1 at /media/christopherskambis/347ed690-d7c2-323f-894e-42d5e488b155: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sdb1" "/media/christopherskambis/347ed690-d7c2-323f-894e-42d5e488b155"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I tried to run fsck on the volume and got the following error: 

```
fsck -fy /dev/sdb1
fsck from util-linux 2.20.1
** /dev/sdb1
** Checking HFS Plus volume.
   Invalid node structure
(3, 0)
** Volume check failed.
```

I'm not sure what to do, and why the DD command didn't work.

---

### Post by SagaciousKJB on 2018-08-21
How did you run the command?  Was the drive you were attempting to clone mounted?  Did you verify the image after copying it with dd?

Not to assume your level of knowledge, but make sure that the disk you're trying to clone isn't mounted and on an active system.  A lot of different things can go wrong trying to clone a disc that has an actively mounted filesystem, like changes to the journal, discrepancies between a mounted and unmounted state, etc.  I don't know the intricacies of HFS to say, but the safe bet is to boot down and start up on a Live CD.  Just so we're on the same page there.

Second, with disk cloning you want to be sure to reference the block device (sda), not the partition(the number after sda).  So what you need to do is...

```
dd if=/dev/sda of=/dev/sdb bs=1m
```

Do not add the partition number.  If you're trying to clone directly from one disk to another that's important, because of certain offsets and things that the journal/catalog records.  They're relative to the start of the disk, but if you tried to transfer /dev/sdb1 to the start of /dev/sdc then you're actually putting the partition onto a block device.  Typically any information a filesystem stores about its inodes will be based on an offset from the disc start, and needs that information, so if you had placed just the HFS partition at the start of a disk it probably wouldn't know what to do with it--again I don't know enough about HFS to say, but this is a common mistake made with dd and disk/image cloning.

So thirdly, let's assume you have all that right, but there could be a problem with your media itself.  Maybe a bad cable, bad drive, bad SATA port.  So the best way to determine if it's a data integrity problem would be to run checksums.  Again you'll need to do this on a LiveCD.

```
md5sum -b /dev/sda > checksum && md5sum -b /dev/sdb
```

If the two checksums are different, then there is a data integrity issue and dd hasn't actually cloned the disk perfectly.  If that's the case then you might want to check out 'ddrescue'.

---

