---
title: "Changing permissions on Fat32 partition"
date: 2006-04-21
forum: Hardware &amp; Laptops
---

### Post by tux-curious on 2006-04-21
I got a new drive the other day and made a fat32 partition whilie reinstalling ubuntu

I can find the hard drive, its mounted, but I can't change the permissions to allow me to write to it.

I tried: (exodus being the name of the partition)
```
sudo chmod 777 /exodus
```

and it waited for a bit but nothing happened, or if it did the permissions didn't change.

Also, I am missing almost a gig on the drive. Its a 1.8G drive, 800M are given up as swap, but I only have 9.3G left. Any ideas on either of my two problems?

---

### Post by devnulljp on 2006-04-21
You want to addd something like this to your /etc/fstab

/dev/hdx1       /some/mount/point     vfat    umask=002,uid=xxx        0       0

where hdx1 is your device in /dev/ and xxx is your user id

or if you don't plan to mount all the time, you can mount with 

pmount /dev/hdx1 /some/mount/point

---

### Post by tux-curious on 2006-04-21
[QUOTE=devnulljp]You want to addd something like this to your /etc/fstab

/dev/hdx1       /some/mount/point     vfat    umask=002,uid=xxx        0       0

where hdx1 is your device in /dev/ and xxx is your user id

or if you don't plan to mount all the time, you can mount with 

pmount /dev/hdx1 /some/mount/point[/QUOTE]
Um, that didn't let me write to the drive, its still mounted in the same place, which is good, but I don't know what changed and thats kinda scary.

So I still can't get it to let non-owner write. I want 777, help?

---

### Post by ruzle0 on 2006-04-21
if you want all users to be able to write to the partition use umask=000

/dev/hdx1 /some/mount/point vfat umask=000 0 0

umask uses the same permisions as chmod, but instead you mark the permisions you want to take away. so with the previous sugestion umask=002 removes the write permision to others and then setting the uid to your user id leaves you with full access. you can also set the group with gid=xxx

---

### Post by troyDoogle7 on 2006-04-21
I didn't know you could put permissions on fat32... I thought you needed ntfs or ext to do it?

---

### Post by ruzle0 on 2006-04-21
the fat files themselves don't have permisions, they will have whatever is given at mount time, which changes if you remount with different options. if mounted by a user then only that user can write to the drive, unless it is told otherwise. fstab is mounted at boot and will have owner as root, unless you use 'uid='
if you have a working fat partition type 'more /etc/fstab' to see you options and 'ls -l' to see the permisions and owner:group of the files

---

### Post by aysiu on 2006-04-21
You can't *chown* a FAT32 partition. It doesn't support Linux permissions (or any permissions, really). In order to access it, you have to mount it properly.

Abbreviated instructions:
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

More detailed instructions:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

