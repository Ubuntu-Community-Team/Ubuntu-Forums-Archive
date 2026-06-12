---
title: "Mounting NTFS netdrive problem"
date: 2010-07-01
forum: Hardware
---

### Post by drorata on 2010-07-01
I have an IOMEGA netdrive which is connected to my router and has the IP: 192.168.1.34

Today, after a long time I didn't use it, I couldn't mount it.
So far it worked in either of the following ways.

**First method**
I have added the file /root/credentials with the following lines:
```
Username=username
Password=password
```
and changed it mode to 700.

In the /etc/fstab I added the line:
```
//192.168.1.34/public /media/public smbfs credentials=/root/credentials, uid=username,gid=username iocharset=utf8 0 0
```
where /media/public is created.

at this point
```
sudo mount -a
```
would mount the netdrive properly.

**Second method**
Added a bookmark
```
smb://192.168.1.34
```
and then open the public directory and using the username and password gain access.

**Nowadays**
I cannot connect using neither of the methods....

When running sudo mount -a, I get:
> mount error(111): Connection refused
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

And when trying to connect using the bookmark, I get:
> Could not open location 'smb://192.168.1.34/'
Failed to retrieve share list from server

Any ideas??

Thanks in advance...

PS: I made no changes to the system, except for regular updates, and problem stays even when loading an older kernel.
I don't know where to start.

PS2: From a different box I can connect to the drive as usual.

---

### Post by drorata on 2010-07-23
bump.... any ideas??

---

### Post by dino99 on 2010-07-23
install mountmanager to deal with it

---

### Post by drorata on 2010-07-23
Thanks for the idea...

Maybe I'll try it some when else, since I found the problem.

Apparently, for some reason, my router gave the *same* address to the external hard drive and to one of my laptops. In order to over come the issue, I shut down everything (HD, laptops and router), and then I turned it back on, in the following order: Router -> External HD -> Laptops.

Thanks again, and all the best,
Dror

---

### Post by IcarusR on 2010-07-23
To prevent this happening you should be able to assign a fixed ip address to your network drive from your router.

---

### Post by drorata on 2010-07-24
Thanks for the tip; I hope I found the way to do it :)

Have a nice weekend!

---

