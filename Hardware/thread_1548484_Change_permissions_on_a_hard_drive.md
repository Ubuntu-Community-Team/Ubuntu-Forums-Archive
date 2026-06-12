---
title: "Change permissions on a hard drive?"
date: 2010-08-08
forum: Hardware
---

### Post by Barney Oatmeal on 2010-08-08
Hello!

      I just added a second hard drive that was NTFS - reformatted to same filetype as Ubuntu uses with GParted.
Now the drive is inaccessible - it shows up, just can't do anything with it because all permissions are set to root.
Can I log into root and change this? If so, how do I log into root? Root doesn't accept my password..........

Thanks and Blessings,
                      Barney Oatmeal

---

### Post by Dylnuge on 2010-08-08
The root account in Ubuntu is by default scrambled. You can use a terminal as root by entering "sudo su" followed by your password. You can chown the files from there. I'm having a similar issue, though, where all the files aare chmoded to 777 and can't be changed (chmod works on them regardless of whether I run it as myself or root, but the files change right back). Hopefully, the chown won't revert on your NTFS drive.

---

### Post by Morbius1 on 2010-08-08
By default a ext3/4 partition will mount with owner and group set to root and with permissions set to 755. Owner can read and write while group and others can only read.

You have 2 ( of many options ):

(1) Change ownership of the mount point.

Let's say, for example, that my username is morbius and that the partition is mounted to /media/Data:
```
sudo chown morbius /media/Data
```This will transfer ownership from root to morbius and morbius will have read / write permissions.

(2) Keep ownership with root but change permissions so everyone can read and write:
```
sudo chmod 0777 /media/Data
```

---

