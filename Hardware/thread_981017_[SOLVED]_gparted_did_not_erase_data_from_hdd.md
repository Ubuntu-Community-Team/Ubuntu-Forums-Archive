---
title: "[SOLVED] gparted did not erase data from hdd"
date: 2008-11-13
forum: Hardware
---

### Post by Cobbs on 2008-11-13
I'm trying to mount a HDD that used to run my OS, since I decided to use a smaller drive.  I used gparted to create a ext3 HDD, yet I am seeing a 7.6GB use of the drive... I assumed that the gparted would have cleaned up and files that were floating around on the HDD when it formatted it, I can't find what it using the space (tried a sudo nautilus to make sure there weren't hidden files).

Any suggestions or ideas why this happened?

Cheers

Cobbs

---

### Post by taurus on 2008-11-13
What's the output of this command from a terminal?

```
df -h
```
You can also format a new harddrive/partition from a terminal too.

---

### Post by Cobbs on 2008-11-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  8.8G   58G  14% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  300K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.8M 1010M   1% /dev
tmpfs                1013M  784K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sdb1             147G  188M  140G   1% /media/disk

---

### Post by taurus on 2008-11-13
> **Cobbs said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              71G  8.8G   58G  14% /
tmpfs                1013M     0 1013M   0% /lib/init/rw
varrun               1013M  300K 1012M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  2.8M 1010M   1% /dev
tmpfs                1013M  784K 1012M   1% /dev/shm
lrm                  1013M  2.0M 1011M   1% /lib/modules/2.6.27-7-generic/volatile
**[COLOR="Blue"]/dev/sdb1             147G  188M  140G   1% /media/disk[/COLOR]**

Are we talking about /dev/sdb1 here?  The thing is empty.  The reason you see 7.6GB of space used with gparted is perhaps due to 5% reserved for ext3 filesystem.

---

### Post by Cobbs on 2008-11-13
Yes, the /dev/sdb1 is the drive in question, is it best to stay with the ext3 partition or go with something else?  I can live with the 5% if need be, I was just wondering if there were leftovers from the old drive that were taking up space.

---

### Post by taurus on 2008-11-13
It's best to stick with ext3 filesystem and once you format it, there is nothing left from previous system.  However, you can set the reserved space to 0% if you wish but since you have a large partition/drive, 147GB, I wouldn't worry too much about that 5%.

---

### Post by Cobbs on 2008-11-13
Ok, excellent, thanks taurus!

---

### Post by prshah on 2008-11-13
> **Cobbs said:**
> is it best to stay with the ext3 partition or go with something else?  I can live with the 5% if need be, 

ext3 is the best option.

That 5% is reserved for root operations when the drive gets full. Typically (for example in Windows) when the drive gets full, you cannot get in even to delete files to create space. To avoid such a situation, ext3 reserves 5% space for usage of root alone. When your harddisk gets full, it's actually 95% full, and critical system processes running as root will continue to function even so. You can also get it as root and delete files to create space.

---

