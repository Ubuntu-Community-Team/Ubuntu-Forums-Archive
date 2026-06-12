---
title: "Strange mdadm warning"
date: 2008-10-01
forum: General Help
---

### Post by BosseGregersson on 2008-10-01
Hello! 

Been using mdadm to setup a raid 1 and that has worked out fine but i do have a strange error that shows up everytime i boot the computer since it gives me a Device Dissapeared error.  The devices work fine though. Anyone have any clues? 

Heres my conf file if that helps
```
server@server:~$ cat /etc/mdadm/mdadm.conf 
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default, scan all partitions (/proc/partitions) for MD superblocks.
# alternatively, specify devices to scan, using wildcards if desired.
DEVICE partitions

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR 

# definitions of existing MD arrays

# This file was auto-generated on Sun, 07 Sep 2008 23:05:48 +0200
# by mkconf $Id: mkconf 324 2007-05-05 18:49:44Z madduck $
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=d8552958:b7966328:01f9e43d:ac30fbff
   devices=/dev/hdb1,/dev/hdd1

```Heres the line i start the daemon with:
```
mdadm --monitor /dev/md0 --daemonise --program /home/server/Desktop/check_raid_status
```

---

