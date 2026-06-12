---
title: "how to give privileges to write on a FAT32 partition mounted"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by markkus80 on 2007-01-04
I have mounted a FAT32 windows partition on a folder in my Ubuntu like this:
sudo mount -t vfat /dev/sda5 /DATA

my problem is that I can read from this /DATA folder but I can not write in it. I've tried to give 777 permissions to this folder but I cant, it neather shows any error message and neather does any change on them.

Can someone help me with this, thanks.

marc

---

### Post by taurus on 2007-01-04
Try

```
sudo umount /dev/sda5
sudo mount -t vfat /dev/sda5 /DATA -o iocharset=utf8,umask=000
```

---

### Post by markkus80 on 2007-01-04
Hi taurus,

its working! Thanks a lot for your fast answer! :) 

marc

---

### Post by taurus on 2007-01-04
You're welcome.

---

### Post by dannyboy79 on 2007-01-04
my gosh, why isn't this stickied or something similar, this has got to be one of the most common things people ask all the time. this and wireless issues.

---

### Post by ajgreeny on 2007-01-04
But surely it's already in the various ubuntu user guides, which can't be too difficult to find if you search a little.
[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_mount.2Funmount_Windows_partitions_.28FAT.29_manually.2C_and_allow_all_users_to_read.2Fwrite)

---

