---
title: "Unusually much disk activity &amp; mount fail"
date: 2010-01-30
forum: Hardware
---

### Post by HakonG on 2010-01-30
I'm running Ubuntu 9.10 on my laptop, and recently there has been constant disk activity, non stop all day (even before i login, at the login screen :???: ). I don't know whats causing this, but i suspect it could be related to the other disk in my computer, which i have Windows 7 x64 installed on, and it fails to mount;
```
schnitzel@pwnsauce:~$ sudo ntfsmount /dev/sdb2
Error opening partition device: Resource temporarily unavailable.
Failed to startup volume: Resource temporarily unavailable.
Failed to mount '/dev/sdb2': Resource temporarily unavailable.
Mount failed.

```

I would appreciate any help, since i'm rather new to Ubuntu :)

---

### Post by IcarusR on 2010-01-30
From ntfsmount manpage...

> ntfsmount device mount_point [-o options]

You need to give a mount point ie

```
sudo ntfsmount /dev/sdb2 /home/user/windows
```

However I don't know if this will resolve your isue

---

### Post by HakonG on 2010-01-30
Thanks for your reply, i tried it, and this is what happened:

```
schnitzel@pwnsauce:~$ sudo ntfsmount /dev/sdb2 /media/windows
fuse: failed to access mountpoint /media/windows: No such file or directory
fuse_mount failed.
Unmounting /dev/sdb2 (Windows 7 (x64))

```

This is strange, mount failed, and then unmounting /dev/sdb2 (Windows 7 (x64)) :???: but it was never mounted.

```

schnitzel@pwnsauce:/media$ ls -l
total 16
lrwxrwxrwx 1 root      root         6 2010-01-15 12:13 cdrom -> cdrom0
drwxr-xr-x 2 root      root      4096 2010-01-15 12:13 cdrom0
drwxr-xr-x 2 root      root      4096 2010-01-15 12:13 cdrom1
drwxr-xr-x 2 root      root      4096 2010-01-19 18:16 Data
drwx------ 2 schnitzel schnitzel 4096 2010-01-24 01:47 truecrypt1
```

```

schnitzel@pwnsauce:/media$ sudo mkdir windows
```

```

schnitzel@pwnsauce:/media$ ls -l
total 20
lrwxrwxrwx 1 root      root         6 2010-01-15 12:13 cdrom -> cdrom0
drwxr-xr-x 2 root      root      4096 2010-01-15 12:13 cdrom0
drwxr-xr-x 2 root      root      4096 2010-01-15 12:13 cdrom1
drwxr-xr-x 2 root      root      4096 2010-01-19 18:16 Data
drwx------ 2 schnitzel schnitzel 4096 2010-01-24 01:47 truecrypt1
**drwxr-xr-x 2 root      root      4096 2010-01-30 18:09 windows**
```

```

schnitzel@pwnsauce:/media$ sudo ntfsmount /dev/sdb2 /media/windows
Error opening partition device: Resource temporarily unavailable.
Failed to startup volume: Resource temporarily unavailable.
Failed to mount '/dev/sdb2': Resource temporarily unavailable.
Mount failed.
schnitzel@pwnsauce:/media$
```

---

### Post by HakonG on 2010-01-30
Its fixed! i edited the /etc/fstab file, there was something about /dev/sdb2 and i removed it, now it mounts properly again :D

but if i want to mount it at boot time (if i understand correctly), i have to put a line in the fstab file.
would this work?
```
/dev/sdb2/ Windows\ 7\ \(x64\)/ ntfs-fuse
```
or
```
/dev/sdb2/ 'Windows 7 (x64)/' ntfs-fuse
``` ?

Edit:
I found the UUID of the partition (FA2877F12877AAF1), should i use that instead?

---

### Post by IcarusR on 2010-01-30
I think /etc/fstab entry should look something like this

```
/dev/sdb2/ /media/windows ntfs 0 0
```

---

### Post by HakonG on 2010-01-30
Thanks! i got it working, and also found out about the mount -a command, lol. i was trying diffirent things in /etc/fstab file and rebooting every time xD saved me many reboots :p

---

