---
title: "Linux jaunty 9.04 shows the Disk for the Partition full out of the Blue..."
date: 2009-08-07
forum: Hardware
---

### Post by rungss on 2009-08-07
My Linux jaunty 9.04 shows the Disk for the Partition full out of the Blue...

The output of the command

```
df -h
```

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda7              74G   70G  271M 100% /
tmpfs                 989M     0  989M   0% /lib/init/rw
varrun                989M  232K  989M   1% /var/run
varlock               989M     0  989M   0% /var/lock
udev                  989M  184K  989M   1% /dev
tmpfs                 989M  116K  989M   1% /dev/shm
lrm                   989M  2.2M  987M   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5              79G   67G   12G  86% /home/bijay/external/Music
/dev/sda6              40G   26G   14G  66% /home/bijay/external/Documents


```

When I ran fsck at Boot time,few Inodes were corrected but when I login, It still show the Problem..

Please Help...

Please let me know if any other info will help...

---

