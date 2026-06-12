---
title: "Trouble setting HDD idle spin down time with rc.local"
date: 2013-11-22
forum: Hardware
---

### Post by Michael_Kearney on 2013-11-22
I have several of the seagate 3TB desktop external drives attached to my home media server and they are always spinning. I have tried setting idle time using this tutorial here: [http://www.howtoeverything.net/linux/hardware/permanently-configure-hard-drives-spin-down-after-given-idle-time](http://www.howtoeverything.net/linux/hardware/permanently-configure-hard-drives-spin-down-after-given-idle-time)

I have edited rc.local and added in lines as follows for the appropiate drives:

```
hdparm -B127 -S120 /dev/disk/by-id/ata-xxxxxxxx_xxxxx
```

but it doesn't seem to be doing anything. when I run hdparm -B /dev/sd? it shows the newer of the drives set to 127 but the other two are still 128. is there something I'm missing? is there something I need to do to "activate" rc.local? I don't have anything else added in rc.local but the first lines are ```
#!/bin/sh -e
#
# rc.local
``` is this something that needs to be uncommented?

---

### Post by Michael_Kearney on 2013-11-22
Here is my rc.local file right now. I've changed a couple idle times just to experiment, as well as setting APM as 255 on the one seagate.
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

#System Drive
hdparm -B127 -S120 /dev/disk/by-id/ata-ST96812AS_5PJ46K48

#Seagate Expansion
hdparm -B255 -S180 /dev/disk/by-id/ata-ST3000DM001-1E6166_Z1F2T7N4

#Seagate Expansion
hdparm -B127 -S120 /dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F00GLT

#Seagate expansion
hdparm -B127 -S120 /dev/disk/by-id/ata-ST3000DM001-9YN166_Z1F028BN


exit 0
```

And this is what I get when I run hdparm -B /dev/sd?

```
michael@michael-MS-7817:~$ sudo hdparm -B /dev/sd?

/dev/sda:
 APM_level    = 254

/dev/sdb:
 APM_level    = not supported

/dev/sdc:
 APM_level    = 127

/dev/sdd:
 APM_level    = 128



```

where sdb is my WD red drive, sdc is my newer seagate drive, and sdd is the older one. I think I should be seeing 127 for both sdc and sdd, right? or 255 for sdc and 127 for sdd since I have since edited rc.local to the above.

And, it seems to spind down after the specified time and just spind right back up again. I even ran hdparm -y /dev/sdc and it spun down and back up again immediately.

---

### Post by tgalati4 on 2013-11-22
Different disk drives means different firmware, so they will behave differently.  If these drives are configured in a RAID pool, then they will spin because the operating system needs to keep track of where all those bits are located on each disk--all of the time.

APM--Advanced Power Management--is an older protocol that has been replaced by other power controls.  So newer drives may not support it, and each drive's firmware handles power management differently.  There may be other tools needed to change drive's behavior.  *hdparm* is a generic hard disk control package and it may not have support for the newest drives.

---

