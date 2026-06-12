---
title: "reinstalled windows xp, no sda1"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by hookem10 on 2007-01-21
I reinstalled windows on the partition that i have for windows, and now i can't find the windows partition at all.
When i search in places>computer it shows filesystem, my external HDD, and the up CD-RW/DVD-ROM drive. I can't find my windows partition.
I figure that i messed that up when i reinstalled windows, any help?
Thanks.

---

### Post by dendy7h on 2007-02-09
I had the same thing happen to me.  I fixed the problem by doing the following.

open the terminal and type the following

```
sudo cp /etc/fstab /etc/fstab.backup
```

then open the device manager

system -> administration -> device manager

scroll down until you see your HD (mine was under SCSI Generic Device) and you will see your partitions there.  Click on "Volume (NTFS)" and click the Advanced tab.  Scroll down until you see volume.uuid (it should be at the bottom).  Highlight and copy the UUID, back to the terminal we go.

type
```
sudo gedit /etc/fstab
```

look in fstab for a line like this

```

# /dev/sda1
UUID=[COLOR="Blue"]FE58D10E58D0C715[/COLOR] /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```

Highlight the UUID and paste.  Save and reboot. :) 

HTH

---

