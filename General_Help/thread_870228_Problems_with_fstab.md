---
title: "Problems with fstab"
date: 2008-07-25
forum: General Help
---

### Post by Sugi on 2008-07-25
I added this line to my fstab last night
.
"/dev/sdb1	/mnt/sdb  	ext3 	rw,users,gid=users 0	1"

It worked prefectly before I reboot today (except I had not write to that partition without sudo).  Now, I can't find the partition in /mnt/sdb/ and I got this error:
$ sudo mount -a
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

What should I do?

Sugi

---

### Post by caljohnsmith on 2008-07-25
You could try running fsck on that partition and see if it can fix the errors:
```
sudo umount /dev/sdb1
sudo fsck /dev/sdb1
```

---

### Post by Sugi on 2008-07-25
I changed this
"/dev/sdb1 /mnt/sdb ext3 rw,users,gid=users 0 1"
to
"/dev/sdb1 /mnt/sdb ext3 noatime 0 1"
and then ran
"sudo mount -a"

Now the sdb partition is mounted, but I still do not have write permission without sudo.

Any ideas?

Thanks,
Sugi

---

### Post by plucky on 2008-07-25
See the Psychocats website for [Mounting Linux Partitions](http://www.psychocats.net/ubuntu/mountlinux) and set them up for use.

Good Luck

---

### Post by caljohnsmith on 2008-07-25
Try using these options in your fstab instead:
```
/dev/sdb1 /mnt/sdb   ext3   defaults,relatime,user
```
"relatime" is the new standard being used in Hardy, and the "defaults" option includes the "rw" option to make the partition read-writable.

---

### Post by Sugi on 2008-09-01
Ummmm... can someone explain this to me?


```
$ sudo mount -a
mount: special device /dev/disk/by-uuid/b3053f5e-64ab-4ea3-9643-c9a56a4e5a1d does not exist
```

Sugi

---

### Post by plucky on 2008-09-02
> **Sugi said:**
> Ummmm... can someone explain this to me?


```
$ sudo mount -a
mount: special device /dev/disk/by-uuid/b3053f5e-64ab-4ea3-9643-c9a56a4e5a1d does not exist
```

Sugi


Output from "man mount" command


 ```
-a     Mount all filesystems (of the given types) mentioned in fstab.
```

Open a terminal and post output of following commands ```
sudo fdisk -l
cat /etc/fstab
ls -l /dev/disk/by-uuid
```

Those are lowercase L not a 1

Good Luck

---

