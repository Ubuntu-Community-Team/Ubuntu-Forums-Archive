---
title: "Stuck with permissions [Only Root can add music to library from Windows drive]"
date: 2008-09-03
forum: General Help
---

### Post by blazemore on 2008-09-03
Exaile won't add music to the collection from the NTFS filesystem I have mounted as /windows, unless I run sudo exaile.

I think this is a problem with permissions.

How can I make it so I don't have to run the program as root (chmod?)

---

### Post by cdtech on 2008-09-03
How is your /etc/fstab setup to mount the partition? or do you manually mount the partition?

**Manual mount:**
```
mount -t ntfs -o rw,uid=1000,gid=100,umask=0022 /dev/**sdb1** /path_to_mount_point
```
(bold is your partition)
You can change the user id and the group id to your liking.
**fstab mount:**
```
**UUID=C6AAD33AAAD325A9** /media/Storage ntfs defaults,umask=002,gid=46 0 2
```
(Use your UUID)

---

### Post by blazemore on 2008-09-03
```
/dev/sda1	/windows	ntfs	users,defaults,umask=000	0	0
```

That's the relevent line from fstab. And I don't know what you mean by UUID. My User ID is 1000

---

### Post by cdtech on 2008-09-03
Give this a shot:
```
/dev/sda1  /windows  ntfs defaults,umask=002,gid=46 0 0
```
My group id for plugdev is:
```
plugdev:x:46
```
You can see your group id's in "/etc/group" just add user's to the group.

---

### Post by blazemore on 2008-09-05
Doesn't matter now, I've migrated to Ubuntu proper. Virtualbox 2.0 came out recently, and I can run my Windows apps on that in Seamless mode

---

