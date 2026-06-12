---
title: "problem mounting external hard drive -ntfs error"
date: 2008-10-13
forum: General Help
---

### Post by jamesey on 2008-10-13
I tried mounting my external HD which and I get this error. I really don't know what it means, and I can't copy and paste the commands it gives me. Figuring out how many underscores are present in my external HD's name is a headache. 

This drive used to mount automatically but I took it to work, used it on a WinXP machine, then brought it home and I see this. 

[IMG]http://i63.photobucket.com/albums/h138/jameseyjamesey/Screenshot-gnome-mount.png[/IMG]

why do I have all these mounts for the same external HD?

[IMG]http://i63.photobucket.com/albums/h138/jameseyjamesey/Screenshot-media-FileBrowser.png[/IMG]

---

### Post by earthpigg on 2008-10-13
super easy solution: plug it back into a windows box, shut the computer down properly.

super FOSS solution: do option #2 as shown in the screen shot you provided.

in the future: dont turn your computer off (linux or windows) without shutting down properly.

:)

---

### Post by bodhi.zazen on 2008-10-13
Or even better, if you do not run windows, do not use ntfs :twisted:

---

### Post by jamesey on 2008-10-13
> **earthpigg said:**
> super easy solution: plug it back into a windows box, shut the computer down properly.

super FOSS solution: do option #2 as shown in the screen shot you provided.

in the future: dont turn your computer off (linux or windows) without shutting down properly.

:)

How can I do option 2 if I can't figure out how many "underscores" to put in my drive name? How do I fix that?

---

### Post by bodhi.zazen on 2008-10-14
> **jamesey said:**
> How can I do option 2 if I can't figure out how many "underscores" to put in my drive name? How do I fix that?

First, make sure the drive is not already mounted 

```
mount
```

Second, I bet you can get rid of all those mount points by rebooting.

Third, make your own mount point :

```
sudo mkdir /meida/ntfs

mount -t nfts-3g /dev/sdb1  /media/ntfs -o gid=1000,uid=100,umask=007,force
```

Note , forcing a mount can (rarely) result in data loss.

---

### Post by brianfreytag on 2008-10-14
> **bodhi.zazen said:**
> First, make sure the drive is not already mounted 

```
mount
```

Second, I bet you can get rid of all those mount points by rebooting.

Third, make your own mount point :

```
sudo mkdir /meida/ntfs

mount -t nfts-3g /dev/sdb1  /media/ntfs -o gid=1000,uid=100,umask=007,force
```

Note , forcing a mount can (rarely) result in data loss.

+1 on being careful when forcing a mount.  It can also corrupt a file system.  I know you're not trying to mount an operating system drive, but I've forced a mount on a Windows partition and it corrupted the file system and I had a 5 hour repair issue.

File system corruption is not fun.

---

### Post by Grez on 2008-10-14
Hi

I'd suggest getting hold of ANY WinXP machine, plug the drive in and then unmount it using the "Remove Hardware" icon in the tray by the clock.

---

### Post by jamesey on 2008-10-15
hmmm, none of these solutions have worked :(

---

### Post by bodhi.zazen on 2008-10-15
> **jamesey said:**
> hmmm, none of these solutions have worked :(

Error message ?

What have you tried exactly ?

---

### Post by jamesey on 2008-10-15
> **bodhi.zazen said:**
> Error message ?

What have you tried exactly ?

**Rebooting** doesn't make all the mount points disappear
**Trying to force boot **gives me the error: unknown system file type "ntfs-3g"

**doing:** 
sudo mount -t ntfs-3g /dev/sdb1 media/My Book________________ -o force
shows me the usage options for "mount"

**Safely removing the device from a windows machine** does nothing. I could still access the files in Windows, so I know the drive is still good. 

I'm so confused.

---

### Post by cariboo on 2008-10-15
Because you have so many disk lables you should use the device number. In a Applications-->Accessories-->Terminal type:

```
sudo fdisk -l
```

This will list all the drives connected to your computer. Paste the results in your next post, so we can give you the exact command to clear up your problem.

Jim

---

### Post by jamesey on 2008-10-15
[IMG][IMG]http://i63.photobucket.com/albums/h138/jameseyjamesey/Screenshot-jamesjamesey.png[/IMG][/IMG]

---

### Post by bodhi.zazen on 2008-10-15
please also post the output of 

```
mount
```

Also, Linux does not like spaces in file names.

You need to either escape them wit a \

like this :

My\ Book________________ 

Or put them in quotes

like this

"My Book________________"

Last, if rebooting did not get rid of all those extra directories, we can manually remove them (we need to make sure nothing is mounted there first).

---

### Post by jamesey on 2008-10-15
```
james@jamesey:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-21-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/james/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=james)
james@jamesey:~$ 

```

---

### Post by bodhi.zazen on 2008-10-15
OK, if you like you can start with :

```
sudo rm -rf /media/My\ Book*
```

Now make a directory

```
sudo mkdir /media/My\ Book
```

And try to mount :

```
sudo mount /dev/sdb1 /media/My\ Book -o force
```

---

### Post by jamesey on 2008-10-15
wow, that worked perfectly!!

---

