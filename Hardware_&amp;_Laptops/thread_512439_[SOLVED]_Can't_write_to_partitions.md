---
title: "[SOLVED] Can't write to partitions"
date: 2007-07-29
forum: Hardware &amp; Laptops
---

### Post by stinkinrich88 on 2007-07-29
Hello!

I have two hard drives with several ext3 partitions and one ntfs partition. I can read all of them but cannot write to any of them. My fstab is this:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2dbc3b47-21ae-4e2b-bc4f-22cd7f10a2df /               ext3    defaults,errors=remount-ro 0       1
# /dev/sdb1
UUID=edf73fb9-3ad7-49c6-9734-18e4cb1d3493 /media/DVDs     ext3    defaults        0       2
# /dev/sda4
UUID=5cd849db-5cd1-4145-b638-c0ea708973ec /media/Data     ext3    defaults        0       2
# /dev/sda2
UUID=54A98654231F56E4 /media/WindowsXP ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=8f5d70e4-5f3f-476d-a739-a4db6a3706ae none            swap    sw              0       0
# /dev/sdb2
UUID=d277c7a7-6102-45fa-8795-5dc11593e5a9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

And when I go to the permissions tab in the properties for the partions it tells me that root is the owner. I've tried changing the fstab to rw but it didn't work. Please help!!


Thanks!!

---

### Post by merlinus on 2007-07-29
For ntfs:

```

sudo apt-get install ntfs-3g ntfs-config

```and then:
```

sudo ntfs-config

```and tick the appropriate boxes.

For the others, try this:

```

sudo chown -R username:username /media/DVDs
sudo chown -R username:username /media/Data

```username is your login

-merlin

---

### Post by stinkinrich88 on 2007-07-29
ahhh! Thanks so much!! i was getting so stressed out! 

anyone else with the same problem, please note to use a : instead of a ; for the chown command.

perfect! Thank you!!

---

