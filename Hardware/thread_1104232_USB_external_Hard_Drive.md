---
title: "USB external Hard Drive"
date: 2009-03-23
forum: Hardware
---

### Post by interse on 2009-03-23
I formatted a WD USB hard drive [120 GB] to Ext.3 
When I plug it in it is recognized, but I cannot write to it as it is owned by root.   I have tried to change the ownership using: sudo chown -R username /dev/sdb1      NOTHING CHANGES re ownership

What am I doing wrong?   Simply want to read and write to the HD.   IF I format it to FAT32 there is no problem, but I would prefer to stay with a linux format.

Using Ubuntu 8:04

---

### Post by cariboo on 2009-03-23
You can't change onwnership of the mount point unless it is in your home directory. You can change permissions of the mount point, you won't own the files, but you will have read/write permissions.

```
sudo chmod -R 777 /mount_point
```

where mount_point is where your drive mounts to typically /media/drive

Jim

---

### Post by vanadium on 2009-03-23
You can change the owner of the moint point if you want to be the sole user of the drive:

```

sudo chown $USER:$USER /mount_point

```

You can determine the mount point in the output of "mount" (look for the entry for /dev/sdb1). It will be a directory under /media.

---

### Post by interse on 2009-03-23
Using "mount" in terminal I get   
   /dev/sdb1 on /media/disk type ext3 (rw,sosuid,nodev,uhelper=hal)

When I type in terminal:
   sudo chmod -R 777 /dev/sdb1
  
    NOTHING CHANGES

When I teyp in terminal:
   sudo chmod -R 777 /media/disk

    NOTHING CHANGES

OBVIOUSLY I AM CONFUSED ABOUT THE COMMAND REQUIRED.

ALSO
   As for sudo chown $USER:$USER /mount_point
  
   AM I CORRECT IN ASSUMING THAT THE FIRST $USER is the previous user, 
   root   and that the SECOND $USER  is my user name?   Also is the $ required or is it a symbol of needed information?

---

### Post by john183 on 2009-03-23
$USER:$USER : The first "$USER" is your user name. The second is actually the group, but in most cases the group name is the same as the user name. if your user name was "aaa" then the command would be:

```
sudo chown aaa:aaa /mount_point
```

---

### Post by interse on 2009-03-24
The advice to use the command:
   
   sudo chown $USER:$USER /mount_point

did not work.   The mount point in my situation is:   /media/disk

I have also tried the command

    sudo chmod -R 777 /mount_point 

Permissions remain the same  "root"  

HELP PLEASE

---

