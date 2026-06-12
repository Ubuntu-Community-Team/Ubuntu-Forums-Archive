---
title: "Parted scripts"
date: 2008-10-26
forum: General Help
---

### Post by blazemore on 2008-10-26
Does Parted (The command-line tool) support scripting?
Can I "queue" a list of commands to run in gparted (before clicking apply) and then run this script on multiple machines?
I've got 32 laptops on which I need to do the exact same thing.
They are all identical.

---

### Post by unutbu on 2008-10-26
Here is a script that uses parted to remove a partition, and create a partition.
Perhaps you can adapt this example to your needs.
```

#!/bin/sh
sudo /etc/init.d/hal stop                            # Stop GNOME from automounting the drive
sudo fdisk -l /dev/sdb
sudo umount /dev/sdb1    
sudo parted /dev/sdb --script print
sudo parted /dev/sdb --script rm 1                   # Removes the first partition, /dev/sdb1
sudo parted /dev/sdb --script print
sudo parted /dev/sdb --script -- mkpart primary 0 -1 # Makes the partition fill the whole disk
sudo parted /dev/sdb --script print
sudo umount /dev/sdb1
sudo mke2fs /dev/sdb1
sudo tune2fs -j /dev/sdb1
sudo fdisk -l /dev/sdb
sudo /etc/init.d/hal start
```

If you "man parted" you will find all the commands available.

---

### Post by ragtag on 2008-10-26
If you're installing all these machines from scratch. Look into using a kickstart file. That way you can set up an unattended install, including disk partitioning, selecting packages and running any script once completed.

Disclaimer: I've only done this on CentOS, but I'm pretty sure it works on Ubuntu too.

---

### Post by blazemore on 2008-10-26
This has nothing to do with Ubuntu per se. It's just I'm using Ubuntu LiveCD because the gParted livecd is a bit crap.
That first idea might be good but I'm a bit rubbish. Is there a way of finding out cylinder numbers etc from gparted? gparted resizes to mb, and parted likes cylinder numbers, right?

---

### Post by blazemore on 2009-01-04
*bump* tiem

---

