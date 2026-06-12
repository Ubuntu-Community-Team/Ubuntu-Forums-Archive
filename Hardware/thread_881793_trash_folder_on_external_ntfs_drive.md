---
title: "trash folder on external ntfs drive"
date: 2008-08-06
forum: Hardware
---

### Post by angelicapple on 2008-08-06
Hi,

I have a 500gb external hard drive, which is formatted in ntfs (so it can also be read from windows). Everything works fine, but I found out that when you delete files from this drive, they are gone permanently (this is apparently working as intended, it has been documented in several places). 

I had the same problem with an internal ntfs drive, but I solved that by changing the /etc/fstab options for the drive to 
```
defaults,umask=007,uid=1000,gid=1000
```
(from defaults,umask=007,gid=46)

Now when I delete something on this internal drive, ubuntu puts it in a hidden trash folder - perfect.

The external drive is working fine, it automounts when I turn it on. There is no line for it in the fstab file.

Now I'm trying to 'fix' my external drive the same way I solved the thrash problem on my internal drive. I added a line to the fstab file:
```
UUID=D0F0C760F0C74B82 /media/noot ntfs rw,suid,dev,exec,noauto,user,async,umask=007,uid=1000,gid=1000 0       1
```
Where /media/noot is where I want it mounted (I created this folder, and did chown -R 777 on it). I'm not using 'defaults' because I want no-auto and user (I guess maybe I could use defaults and just put those two parameters behind that? My knowledge of these kind of things is kinda limited)

However now when I try to mount it, ubuntu says I can't, because 'unprivileged users can't mount this drive'.

Any hints anyone? I don't care in what manner, but I want it so that when I delete something on my external drive, it goes to any trash folder (preferably on that drive, otherwise on my filesystem somewhere).

---

### Post by angelicapple on 2008-08-07
Anyone? :(

---

