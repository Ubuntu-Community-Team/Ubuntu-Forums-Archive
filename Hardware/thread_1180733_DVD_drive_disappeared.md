---
title: "DVD drive disappeared"
date: 2009-06-07
forum: Hardware
---

### Post by Shadowfaux on 2009-06-07
Hey, I'm having probelms with my dvd drive on jaunty, the problem is that ubuntu doesn't recognise it as being there.

I've had it setup before and it was playing and mounting, but now its not there at all, not even under sudo fdisk -l. I know it still has power to it because i can get it to open and close, but as I said, its not being listed.

here is my fstab:
```

proc            /proc           proc    defaults        0       0
 /dev/sda1
UUID=778617e6-6be6-45d9-8e8c-2e06b121ec9f /               ext3    relatime,errors=remount-ro 0       1
 /dev/sda5
UUID=12eb80c4-43cd-45e9-b846-bfd6b0ed7f46 none            swap    sw              0       0
/dev/scd0  /media/cdrom  udf,iso9660  user,noauto,exec,utf8  0  0
/dev/sdc1	/media/xp	ntfs	user,auto,rw		0	0
/dev/sdb1	/media/storage	ext3	user,auto,rw		0	0
/dev/sdd1	/media/usb	vfat  user,auto,rw		0	0	

```
and here is my output from sudo fdisk -l
```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000cc594

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2eec38c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee3cee3c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    b  W95 FAT32

```

and finally the output from sudo mount /dev/scd0

```
mount: special device /dev/scd0 does not exist
```

I haven't changed anything recently, so i'm really unsure what has happened.

All and any help is greatly appreciated.

---

### Post by Dscottmc7 on 2009-12-15
Shadowfox...
Surprised no one has responded to this!  I've read no less than 30 NEW instances of upgrades (8.04 to 9.10) causing the CDROM to cease functioning.  Some concluded it was the DMA not turned on, others said it had to be on...some said it was the "new" upgrade code.  There were as many answers as there were questions and in each case it ended up either saying, "OK, Then I'll label this bug as being fixed!"  OR concluding something that was isolated (meaning concluding it was an HP Pavilion 1243x hardware problem...) when 12 others with 12 totally different pieces of hardware were experiencing the same thing.

Here's the deal.  For some reason with the upgrade to 8.04 AND the upgrade to 9.04 the CDROM ceases to function...EXCEPT for the reality that it will sense the current 9.04 DVD, boot from it, read it, etc., but no other.   Jaunty doesn't "see" it. 

I've gone through everything everyone has said and finally concluded (PLEASE HELP ME IF ANYONE CAN) that I need the Windows Driver specific for the HP CDROM to go forward.

Theory:  I would assume that I need to be operating Windows to install that driver.  None of the emulators will install that driver.  I have been full time/exlusive Ubuntu since the beginning...a total convert from Windows.  Any Ideas, Anyone?

Just to let you know, good buddy, that your words have not fallen on deaf ears!

Scott

---

### Post by thewho443 on 2009-12-19
I'll go ahead and bump this since I've been having the same problem for over a month and I've tried every suggested fix that I could find on here to no avail.  Hopefully someone can figure this out before I have to do something drastic like watch my movies on windows...

---

