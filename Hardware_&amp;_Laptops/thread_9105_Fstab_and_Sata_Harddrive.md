---
title: "Fstab and Sata Harddrive"
date: 2004-12-24
forum: Hardware &amp; Laptops
---

### Post by darkoptix on 2004-12-24
I'm having troubles with my SATA harddrive and getting it to automount through the fstab.
The sata drive holds my windows install, while a ide holds my ubuntu install. My Fstab look like this:
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc        /media/cdrom1   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1       /mnt/windows    ntfs    umask=0222      0       0

It says the special device cannot be found. Now the trouble i'm having is when its all done loading, and I restart the fstab(sudo mount -a) The windows partition works fine.

Is it not loading the modules before the fstab? Anyway around this.

---

### Post by jackmacokc on 2005-01-20
i have the EXACT same problem and get the exact same error...my ide drive is drive 0, my sata is drive 1...win on sata, ubuntu on ide....

i've done a lot of asking around in irc, and posting, and the general consensus is that the only way to work around this is to recompile the kernel. apparently, the sata drives are attempting to be mounted before the sata module is loaded.

bummer huh?

i dont know anything about recompiling the kernel, but my buddy is going to help me do it in the next few days. if you'd like i'll try to post some detail about what we do.

---

### Post by daniels on 2005-01-20
The problem seems to be when you boot off CD, the BIOS boot order is CDROM, IDE, SATA, so SATA is the second fixed disk.  When you don't, the BIOS tells you that it's SATA, IDE, CDROM, so SATA is the *first* fixed disk.  It's a very hard problem to solve.

---

### Post by jackmacokc on 2005-01-21
That doesnt make any sense - if SATA is the first fixed disk, why wouldnt these disks mount at bootup?

---

