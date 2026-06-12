---
title: "2nd HDD issues"
date: 2011-02-25
forum: Hardware
---

### Post by macd0g on 2011-02-25
hi, i run a computer solely on ubuntu 10.10, and have a secondary 500gb hdd for all my music, photos etc,
now, whenever i reboot the computer, programs like rhythmbox no longer sees this hdd until i click "places/new volume", then a 'new volume" icon appears on the desktop, and rhythmbox sees all my music.  same thing goes for shotwell.
is there a way for the computer to automatically do this to save me having to do this every time.
i want to use disk utility, but i am a bit scared of it incase i wipe my data, as there is no other way of backing this up at the moment.  
any ideas?

---

### Post by IcarusR on 2011-02-26
To get your second drive to auto mount if it is internal you need to add a line to /etc/fstab as described here...

[https://help.ubuntu.com/community/AutomaticallyMountPartitions]("https://help.ubuntu.com/community/AutomaticallyMountPartitions")

---

### Post by macd0g on 2011-03-03
wow, now i am really lost,
so this is my "sudo fdisk -l"

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006d650

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9347    75078656   83  Linux
/dev/sda2            9348        9730     3069953    5  Extended
/dev/sda5            9348        9730     3069952   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x5f24401e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4872    39128641    7  HPFS/NTFS
/dev/sdb2            4872        9730    39020544    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3baafbfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488383488    7  HPFS/NTFS
monkey@monkey:~$


i am trying to automatically mount /dev/sdc1

i also dont seem to be able to view the 'permissions' when i right hand click on the "new volume" icon.  
hmmmmm......

---

