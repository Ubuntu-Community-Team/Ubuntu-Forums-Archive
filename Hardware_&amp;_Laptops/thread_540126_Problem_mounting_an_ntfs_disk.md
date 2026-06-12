---
title: "Problem mounting an ntfs disk"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by bobthebullet990 on 2007-09-01
Hi all... I really really really need to mount this disk as it contains a lot of data I need! ...I recently moved from win XP to Linux, hence the reason why its formatted as an ntfs partition! ...I have gone through the steps to install ntfs-3g to support ntfs partitions, and it worked fine. HOwever, when mounting the disk, it told me that line 11 in /etc/fstab was bad, I copied it exactly as from the website...

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f56f8f56-900b-4556-8395-53c03ce9351a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=5d4cd63c-1668-4609-9ffe-b7bc37acfac5 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660    user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660    user,noauto     0       0
/dev/           /media/floppy0  auto    rw,    user, noauto    0       0
/dev/hdb1       /media/docs     ntfs-3g        defaults,locale=en_US.utf8   0    0

```

Can anyone see why this is "bad"? - Is it because the floppy device has not been specified? ...this was already like this, and my system does not have a floppy, so I guess I can just delete this line?

Also... after this error, came the error:

```

Failed to mount '/dev/hdb1': Operation not supported
Mount is denied because the NTFS journal file is unclean. Choices are:
 A) Shutdown Windows properly.
 B) Click the 'Safely Remove Hardware' icon in the Windows taskbar
    notification area before disconnecting the device.
 C) Use 'Eject' from Windows Explorer to safely remove the device.
 D) If you ran chkdsk previously then boot Windows again which will
    automatically initialize the journal.
 E) Run 'ntfsfix' on Linux which will reset the NTFS journal.
 F) Mount the volume read-only by using the 'ro' mount option.

```

So I went and downloaded ntfsfix and ran, which gave me:

```

matt@matt-desktop:~$ ntfsfix /dev/hdb1
Mounting volume... FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Permission denied
Volume is corrupt. You should run chkdsk.

```

Although, I cannot run chkdsk as I no longer have win XP installed!

Does anyone have any ideas? thanks!

---

### Post by bobthebullet990 on 2007-09-01
Dont worry anyone! I managed to fix it! ...Its now mounted!

---

