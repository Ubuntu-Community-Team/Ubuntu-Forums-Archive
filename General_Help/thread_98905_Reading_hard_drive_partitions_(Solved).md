---
title: "Reading hard drive partitions (Solved)"
date: 2005-12-04
forum: General Help
---

### Post by Minn3h on 2005-12-04
I recently bought a 250GB hdd for additional storage but also so I could start playing around with Linux.  I'm dual booting Ubuntu and XP Pro so I would like to have a partition read/writable by both OSs.  I was under the impression fat32 was such a filesystem.  So of that 250GB, 50 is my Ubuntu partition and 200 is a fat32 partition.  The problem is I don't know how to go about mounting that partition.  In the Disks under Administration it says that partition is at /dev/hdb3 but I am unable to "Enable" it.  Filesystem is Windows Virtual FAT (vfat). Access path is none, and I wouldn't know what path to specify.  Thanks for the help.

---

### Post by doitashimashite on 2005-12-04
sudo gedit /etc/fstab

Add the line

/dev/hdb3 /mnt/hdb3 vfat noauto,user,uid=<your user id>,gid=users

or change the line if there is already an entry for /dev/hdb3.
Also, change the mount point /mnt/hdb3 in this example to the directory of choice.

Finally, (re)mount /dev/hdb3.

---

### Post by Minn3h on 2005-12-04
What's the user id that I need to put in there?

Also, when I try to mount it (without that one option in fstab since I don't know what user id) it says:
mount: mount point /media/hdb3 does not exist

---

### Post by aysiu on 2005-12-04
If you're sure it's /dev/hdb3, follow these directions exactly. The only thing you can modify safely is changing *sharedddocs* to some other name you find more convenient, but you have to change the name in both places in the instructions.

```
sudo umount /dev/hdb3
sudo mkdir /shareddocs
sudo cp /etc/fstab /etc/fstab_backup
sudo gedit /etc/fstab
``` Delete any line that references /dev/hdb3 and replace it with this one ```
/dev/hdb3  /shareddocs  vfat   umask=000   0  0
``` Then save. ```
sudo mount -a
```

---

### Post by Minn3h on 2005-12-04
That worked, thanks.

---

