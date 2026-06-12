---
title: "Backing up Ubuntu,on a external?"
date: 2008-10-29
forum: General Help
---

### Post by LukeRocksALot on 2008-10-29
Hi,i was wondering if i would be able to backup everything from ubuntu to a external HDD,and then put the ubuntu backup on another pc,and if so how?Thanks!BTW im using wubi.

---

### Post by alienprdkt on 2008-10-29
BACKUP YOUR MBR
    You should do this before you edit your partition table so that you can put it back if you mess things up.

    # dd if=/dev/hda of=/root/hda.boot.mbr bs=512 count=1
    If things mess up, you can boot with Knoppix, mount the partition containing /root (hda1 in this example) and put back the MBR with the command:
    # dd if=/mnt/hda1/root/hda.boot.mbr of=/dev/hda bs=512 count=1 

Then you can back up drive and pipe it through gunzip 

# dd if=/dev/hda3 | gzip -c | split -b 2000m - <point to external device>

To restore the multi-file backup, do the following:
# cat /mnt/hdc1/backup.img.gz.* | gzip -dc | dd of=<point to external device>

---

