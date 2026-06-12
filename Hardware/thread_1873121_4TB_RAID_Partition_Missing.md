---
title: "4TB RAID Partition Missing"
date: 2011-10-31
forum: Hardware
---

### Post by wide_load on 2011-10-31
Hey,

So a while ago with the upgrade to 10.04 my 4TB RAID 1 partition stopped mounting at boot, I had to open GParted and let it scan the drives before it would mount (weird).

Now with the upgrade to 11.10 the same partition does not mount at all, I cant get it to mount by toggling the raid flag for the partition in GParted and them running 

```
mount /dev/mapper/sil_bgadejajfgbb1 /some/location
```This technically works (as in I can list the content of the drive), but after doing this my system becomes massively unresponsive and only updates the screen once every 15 seconds or so. Unmounting the drive stops this happening.

If the raid flag is not toggled in GParted, then dmraid does not discover any partitions (it's not the mounting the fails, there is nothing to mount) as shown below.

```
Jacek@local: ~ $ sudo dmraid -ay -vvv -d -i
NOTICE: /dev/sdd: asr     discovering
NOTICE: /dev/sdd: ddf1    discovering
NOTICE: /dev/sdd: hpt37x  discovering
NOTICE: /dev/sdd: hpt45x  discovering
NOTICE: /dev/sdd: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sdd: jmicron discovering
NOTICE: /dev/sdd: lsi     discovering
NOTICE: /dev/sdd: nvidia  discovering
NOTICE: /dev/sdd: pdc     discovering
NOTICE: /dev/sdd: sil     discovering
NOTICE: /dev/sdd: via     discovering
NOTICE: /dev/sdc: asr     discovering
NOTICE: /dev/sdc: ddf1    discovering
NOTICE: /dev/sdc: hpt37x  discovering
NOTICE: /dev/sdc: hpt45x  discovering
NOTICE: /dev/sdc: isw     discovering
DEBUG: not isw at 500107860992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 500106779136
NOTICE: /dev/sdc: jmicron discovering
NOTICE: /dev/sdc: lsi     discovering
NOTICE: /dev/sdc: nvidia  discovering
NOTICE: /dev/sdc: pdc     discovering
NOTICE: /dev/sdc: sil     discovering
NOTICE: /dev/sdc: via     discovering
NOTICE: /dev/sdb: asr     discovering
NOTICE: /dev/sdb: ddf1    discovering
NOTICE: /dev/sdb: hpt37x  discovering
NOTICE: /dev/sdb: hpt45x  discovering
NOTICE: /dev/sdb: isw     discovering
DEBUG: not isw at 2000398932992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 2000397851136
NOTICE: /dev/sdb: jmicron discovering
NOTICE: /dev/sdb: lsi     discovering
NOTICE: /dev/sdb: nvidia  discovering
NOTICE: /dev/sdb: pdc     discovering
NOTICE: /dev/sdb: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sdb: sil metadata discovered
NOTICE: /dev/sdb: via     discovering
NOTICE: /dev/sda: asr     discovering
NOTICE: /dev/sda: ddf1    discovering
NOTICE: /dev/sda: hpt37x  discovering
NOTICE: /dev/sda: hpt45x  discovering
NOTICE: /dev/sda: isw     discovering
DEBUG: not isw at 2000398932992
DEBUG: isw trying hard coded -2115 offset.
DEBUG: not isw at 2000397851136
NOTICE: /dev/sda: jmicron discovering
NOTICE: /dev/sda: lsi     discovering
NOTICE: /dev/sda: nvidia  discovering
NOTICE: /dev/sda: pdc     discovering
NOTICE: /dev/sda: sil     discovering
NOTICE: sil: areas 1,2,3,4[4] are valid
NOTICE: /dev/sda: sil metadata discovered
NOTICE: /dev/sda: via     discovering
DEBUG: _find_set: searching sil_bgadejajfgbb
DEBUG: _find_set: not found sil_bgadejajfgbb
DEBUG: _find_set: searching sil_bgadejajfgbb
DEBUG: _find_set: not found sil_bgadejajfgbb
NOTICE: added /dev/sdb to RAID set "sil_bgadejajfgbb"
DEBUG: _find_set: searching sil_bgadejajfgbb
DEBUG: _find_set: found sil_bgadejajfgbb
DEBUG: _find_set: searching sil_bgadejajfgbb
DEBUG: _find_set: found sil_bgadejajfgbb
NOTICE: added /dev/sda to RAID set "sil_bgadejajfgbb"
DEBUG: checking sil device "/dev/sda"
DEBUG: checking sil device "/dev/sdb"
DEBUG: set status of set "sil_bgadejajfgbb" to 16
RAID set "sil_bgadejajfgbb" was activated
INFO: Activating stripe raid set "sil_bgadejajfgbb"
NOTICE: discovering partitions on "sil_bgadejajfgbb"
NOTICE: /dev/mapper/sil_bgadejajfgbb: dos     discovering
DEBUG: freeing devices of RAID set "sil_bgadejajfgbb"
DEBUG: freeing device "sil_bgadejajfgbb", path "/dev/sda"
DEBUG: freeing device "sil_bgadejajfgbb", path "/dev/sdb"
Jacek@local: ~ $ ll /dev/mapper/
total 0
crw------- 1 root root 10, 236 2011-10-31 15:58 control
lrwxrwxrwx 1 root root       7 2011-11-01 00:55 sil_bgadejajfgbb -> ../dm-0

```Any advice would be awesome, I have a fair bit of Linux experience, but have no idea where to start with this one !

---

### Post by wide_load on 2011-11-06
Minor update: I think the unresponsiveness was caused by a bad drive that was not part of the RAID array.

Still, any idea how to get this to mount automatically ?

---

### Post by wide_load on 2012-03-05
Sorry to dig up an old topic but I still have no solution for this.

I have done a bit more testing though and worked out that if I recreate the raid device with the cards POST interface gParted will see the 4TB disk just fine, it will also create a partition table on it and after rebooting it will still see that table.

When creating a partition though it appears to go through the process and completed, an entry for the partition is created in /dev/mapper. The odd thing is that after a reboot this entry is missing and only the disk is visible in /dev/mapper but gParted still sees the partition on the disk (with an error because it's somehow missing)

Any ideas would be greatly appreciated as I'm pretty much lost with this now.

---

### Post by wide_load on 2012-03-05
Right I changed my search terms and found this [http://ubuntuforums.org/showthread.php?t=1719850&page=2](http://ubuntuforums.org/showthread.php?t=1719850&page=2) following the advice and adding the ppa to update dmraid the drive now mounts perfectly. :D

---

