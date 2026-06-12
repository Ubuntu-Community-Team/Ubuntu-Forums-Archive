---
title: "mount harddisk with ubuntu 8.04 live cd"
date: 2008-11-22
forum: Hardware
---

### Post by abovenewbi on 2008-11-22
ok, My computer crashed! my hard disk has window vista and it "crashed" , basically i can't access my files, so now
i am booting ubuntu live to see if i can access my files on sda1 and copy them to my external hard disk, however i get this error message:
$LogFile indicates unclean shutdown (0, 0) Failed to mount '/dev/sda1'; Operation not support Mount is denied because NTFS is marked to be in use.

how do i mount the hard disk? what are the comands so i can do it on the command line? any suggestions will be highly appreciated,

---

### Post by taurus on 2008-11-22
Applications -> Accessories -> Terminal
```
sudo mkdir /media/windows
sudo mount -t ntfs-3g /dev/sda1 /media/windows -o force
df -h
```

---

### Post by abovenewbi on 2008-11-22
ok, when i do the command a "help" menu appears and nothing happens
it says:
so far the information part. Next the mounting.
the command is mount [-t ftype] something somewhere.

details found in /etc/fstab may be omitted.
mount -a [-t]

and so on......

---

### Post by taurus on 2008-11-22
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```
That should be lower case letter L, not number 1.

---

