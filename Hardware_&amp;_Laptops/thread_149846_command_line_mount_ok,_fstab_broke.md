---
title: "command line mount ok, fstab broke?"
date: 2006-03-24
forum: Hardware &amp; Laptops
---

### Post by morguns on 2006-03-24
why is it i can mount a simpletech nas drive via command line but not in fstab? here are the commands i'm using:

at command line (works):```
sudo mount -t nfs 192.168.1.9:/path/to/share /mnt/point
```in /etc/fstab (doesn't work):```
192.168.1.9:/path/to/share  /mnt/point     nfs     rw,hard,intr 0 0
```

---

### Post by skirkpatrick on 2006-03-24
I have the same problem with Samba mounts.  I almost wonder if the network isn't fully up before fstab is processed.  And it doesn't matter if I'm setup for DHCP or static IP either.

---

### Post by morguns on 2006-03-25
interesting you mention that. in searching these forums i ran across [another thread]("http://www.ubuntuforums.org/showthread.php?t=149287&highlight=fstab") talking about it. didn't make much sense to me, but perhaps that's a direction to follow?

---

### Post by terminalspin on 2006-03-26
I had been struggling with a similar problem; If I mount the network shares from the command line, it works fine - but if I add the filesystems to fstab, they (almost) all timeout on booting up.

One of the threads on here - [http://ubuntuforums.org/showthread.php?t=83374]("http://ubuntuforums.org/showthread.php?t=83374")  suggested using the tcp option on the fstab line, and it seems to have done the trick here.

---

### Post by skirkpatrick on 2006-03-26
Trying that out...


Nope, still didn't help.  Here's my line in fstab:
//Warren/Public	/mnt/Public	smbfs	proto=tcp,user,noatime,username=smbguest,password="smbguest",dmask=0777,fmask=0777

---

