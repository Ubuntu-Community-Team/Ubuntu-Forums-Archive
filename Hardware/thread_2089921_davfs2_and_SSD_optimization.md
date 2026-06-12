---
title: "davfs2 and SSD optimization"
date: 2012-11-30
forum: Hardware
---

### Post by victorbrca on 2012-11-30
I'm synching a folder in my SSD to box.com via davfs2, however it does not support 'noatime' or 'nodiratime' for mounting the file system. Is there anything I can/should do to optimize my SSD usage? 

```
# / was on /dev/sda3 during installation
UUID=9c2281d0-dae9-4d26-a9d6-94730274341e /               ext4    discard,noatime,nodiratime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=21f37919-e73a-4ece-9282-1deb39e1b6f6 /home           ext4    discard,noatime,nodiratime,defaults        0       2
# /mnt/ntfs was on /dev/sda5 during installation
UUID=207EFD7475D24982 /mnt/ntfs       ntfs    discard,noatime,nodiratime,defaults,umask=007,gid=46 0       0
# /mnt/ssdi was on /dev/sdb2 during installation
UUID=3305B7BA7D314DF3 /mnt/ssdi       ntfs    discard,noatime,nodiratime,defaults,umask=007,gid=46 0       0
# /mnt/windows8 was on /dev/sda2 during installation
UUID=964214C34214A9CF /mnt/windows8   ntfs    discard,noatime,nodiratime,defaults,umask=007,gid=46 0       0
# swap was on /dev/sdb1 during installation
UUID=f11138b4-2aad-4738-a7c7-dbf46700c119 none            swap    sw              0       0
# tells fstab to mount /tmp in the ram
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
# Mounts Box.com
https://www.box.com/dav /home/victor/Box davfs _netdev,rw,user 0 0
```

Thanks,
Vic.

---

