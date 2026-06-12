---
title: "Can't access directories in home/"
date: 2012-01-13
forum: Hardware
---

### Post by xtheunknown0 on 2012-01-13
Hello,

I have successfully backed up needed files from the Windows 7 partition that was in an internal SATA (of a "broken laptop" - won't boot).

But, Windows XP on this machine doesn't see Linux stuff, so I figured I'd run Ubuntu 10.04 (for this post) from a live CD to see all partitions. Turns out I can, but after cd'ing to
```

/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home

```
, I fail to access either of (from ls)
```

user
xtheunknown0

```
Ie. After
```

cd user/

```
I get
```

bash: cd: user: Permission denied.

```
From nautilus, there is a silvery thick cross on the bottom right corner of the user folder.

I'd like to backup user/ ; how???

TIA,
xtheunknown0

---

### Post by sanderd17 on 2012-01-13
> **xtheunknown0 said:**
> Hello,

I have successfully backed up needed files from the Windows 7 partition that was in an internal SATA (of a "broken laptop" - won't boot).

But, Windows XP on this machine doesn't see Linux stuff, so I figured I'd run Ubuntu 10.04 (for this post) from a live CD to see all partitions. Turns out I can, but after cd'ing to
```

/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home

```
, I fail to access either of (from ls)
```

user
xtheunknown0

```
Ie. After
```

cd user/

```
I get
```

bash: cd: user: Permission denied.

```
From nautilus, there is a silvery thick cross on the bottom right corner of the user folder.

I'd like to backup user/ ; how???

TIA,
xtheunknown0

How is the b1d7dd6b-db4f-4137-9c03-a37cb21b03da drive partitioned? Can you check gparted to see if it's ext3, ext4 or maybe NTFS of FAT?

I suppose it's ext4, that means files have permissions. Can I see the permissions of the user directory?

```

ls -l /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home/user

```

---

### Post by xtheunknown0 on 2012-01-13
> **sanderd17 said:**
> How is the b1d7dd6b-db4f-4137-9c03-a37cb21b03da drive partitioned? Can you check gparted to see if it's ext3, ext4 or maybe NTFS of FAT?
ext4
> I suppose it's ext4, that means files have permissions. Can I see the permissions of the user directory?

```

ls -l /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home/user

```

In home/, ls -l outputs
```

total 8
dr-x------ 2 1001 1001 4096 2011-07-10 09:24 user
dr-x------ 3 1000 1000 4096 2011-07-06 17:53 xtheunknown0

```

and ls -l user/ outputs
```

ls: cannot open directory user/: Permission denied

```

xtheunknown0

---

### Post by sanderd17 on 2012-01-13
> **xtheunknown0 said:**
> ext4


In home/, ls -l outputs
```

total 8
dr-x------ 2 1001 1001 4096 2011-07-10 09:24 user
dr-x------ 3 1000 1000 4096 2011-07-06 17:53 xtheunknown0

```

and ls -l user/ outputs
```

ls: cannot open directory user/: Permission denied

```

xtheunknown0

I guess you can change the rights to a better level. You see only user with id 1001 (that's normally the first general user created) can read the user directory. I think you could do

```

sudo chmod a+r -r user
sudo chmod u+w -r user

```

That will give read rights to all users (a+r) and write rights to the owner (u+w). Listing a directory asks for the execute (x) right, so you may also need to do

```

sudo a+x directory_to_be_modified

```

on each directory. I can't do this recursively since the files don't need the x-permission.

For more information about Unix file permissions, see this: [http://linuxcommand.org/lts0070.php](http://linuxcommand.org/lts0070.php)

---

### Post by xtheunknown0 on 2012-01-13
I'm now trying to follow instructions at [http://ubuntuforums.org/showpost.php?p=11079356&postcount=4](http://ubuntuforums.org/showpost.php?p=11079356&postcount=4)

Here's my output:
```

xtheunknown0@xtheunknown0-laptop:~$ sudo su
root@xtheunknown0-laptop:/home/xtheunknown0# D=/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/
root@xtheunknown0-laptop:/home/xtheunknown0# mount -o bind /dev $D/dev
root@xtheunknown0-laptop:/home/xtheunknown0# mount -o bind /dev $D/dev
root@xtheunknown0-laptop:/home/xtheunknown0# mount -t sysfs none $D/sys
mount: none already mounted or /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da//sys busy
mount: according to mtab, none is already mounted on /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/sys
root@xtheunknown0-laptop:/home/xtheunknown0# mount -o bind /dev/shm $D/dev/shm
root@xtheunknown0-laptop:/home/xtheunknown0# mount -t proc none $D/proc
mount: none already mounted or /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da//proc busy
mount: according to mtab, none is already mounted on /media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/proc
root@xtheunknown0-laptop:/home/xtheunknown0# chroot $D
root@xtheunknown0-laptop:/# ecryptfs-mount-private 
ERROR: Encrypted private directory is not setup properly

```
Why don't I get an opportunity to enter a password?

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2012-01-14
Bump

---

### Post by sanderd17 on 2012-01-15
It's a problem with permissions. Not with encription/decription.

Please try the things I said before.

---

### Post by xtheunknown0 on 2012-01-15
> **sanderd17 said:**
> It's a problem with permissions. Not with encription/decription.

Please try the things I said before.

What have I done wrong?
```

xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l
total 8
d--x------ 2         1001         1001 4096 2012-01-14 09:18 user
d--x------ 3 xtheunknown0 xtheunknown0 4096 2011-07-07 03:53 xtheunknown0
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod a+r -R user/
[sudo] password for xtheunknown0: 
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod u+w -R user/
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod a+x -R user/
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls user/
Access-Your-Private-Data.desktop  README.txt
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l user/
total 0
lrwxrwxrwx 1 1001 1001 56 2011-07-10 19:24 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 1001 1001 52 2011-07-10 19:24 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l
total 8
drwxr-xr-x 2         1001         1001 4096 2012-01-14 09:18 user
d--x------ 3 xtheunknown0 xtheunknown0 4096 2011-07-07 03:53 xtheunknown0

```

TIA,
xtheunknown0

---

### Post by xtheunknown0 on 2012-01-16
Bump

---

### Post by sanderd17 on 2012-01-16
> **xtheunknown0 said:**
> What have I done wrong?
```

xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l
total 8
d--x------ 2         1001         1001 4096 2012-01-14 09:18 user
d--x------ 3 xtheunknown0 xtheunknown0 4096 2011-07-07 03:53 xtheunknown0
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod a+r -R user/
[sudo] password for xtheunknown0: 
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod u+w -R user/
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ sudo chmod a+x -R user/
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls user/
Access-Your-Private-Data.desktop  README.txt
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l user/
total 0
lrwxrwxrwx 1 1001 1001 56 2011-07-10 19:24 Access-Your-Private-Data.desktop -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop
lrwxrwxrwx 1 1001 1001 52 2011-07-10 19:24 README.txt -> /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt
xtheunknown0@xtheunknown0-laptop:/media/b1d7dd6b-db4f-4137-9c03-a37cb21b03da/home$ ls -l
total 8
drwxr-xr-x 2         1001         1001 4096 2012-01-14 09:18 user
d--x------ 3 xtheunknown0 xtheunknown0 4096 2011-07-07 03:53 xtheunknown0

```

TIA,
xtheunknown0

As you can ls the user directory, I assume you can also cd to it, or not?

I see there are two files in user: one that links to /usr/share/ecryptfs-utils/ecryptfs-mount-private.desktop, and one that links to /usr/share/ecryptfs-utils/ecryptfs-mount-private.txt.

by looking at the file names, I wouldn't be surprised if this is a result from your attempts to mount this as an encrypted drive.

If this is the case, I don't know where your files have gone.

---

