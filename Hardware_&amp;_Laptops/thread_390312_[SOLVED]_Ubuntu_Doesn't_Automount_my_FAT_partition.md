---
title: "[SOLVED] Ubuntu Doesn't Automount my FAT partition!"
date: 2007-03-21
forum: Hardware &amp; Laptops
---

### Post by Megaqwerty on 2007-03-21
This has been a HUGE annoyance. My computer used to automatically mount all of my non-Ubuntu partitions.

sda1, sda2, and sda5

sda1 = FAT32
sda2 = NTFS
sda5 = FAT32

However, after I defragged the sda5 drive (admittedly, while stuck in Windows) the drive doesn't automatically mount at startup.

Now, I have to resort to running
```
sudo mount /dev/sda5 /media/sda5
```
I don't get the convince of having it listed in "My Places" and I can't edit my files unless I'm doing it as root. I've tried to do
```

sudo su
chown megaqwerty /media/sda5 
```

But it tells me:
```
chown: changing ownership of `/media/sda5': Operation not permitted 
```

Operation not permitted?!?!?? I am ROOT!

Sorry, this is frustrating, but the question still stands.

Can anyone help me get this working just like it did in the past? (Automount at startup, read/write/execute permissions given to megaqwerty, etc.)

Thanks,

Megaqwerty

---

### Post by taurus on 2007-03-21
Edit /etc/fstab with

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/fstab
```
and add these lines to the end of it.

```
/dev/sda1   /media/sda1   vfat   iocharset=utf8,umask=000   0  0
/dev/sda2   /media/sda2   ntfs   nls=utf8,umask=0222   0   0
/dev/sda5   /media/sda5   vfat   iocharset=utf8,umask=000   0  0
```
Save the chances.  Then, create those three new mount points and mount them

```
sudo mkdir /media/sda1 /media/sda2 /media/sda5
sudo mount -a
df -h
```
Or reboot.

---

### Post by Megaqwerty on 2007-03-21
Actually, my /etc/fstab file still has entries for the disks. Oh, and only sda5 isn't mounting.

Here is my /etc/fstab file.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=6ffdb2ba-16c5-4a57-95da-b10b3e57e229 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=07D5-0810  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=D6E02017E01FFBFD /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=44D7-133E  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=6d03716b-b380-463e-a6c2-bc6db2a8ea27 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Also, I figured I'd try doing 

```
 sudo mount -a 
```

but it gave me this:

```
 mount: special device /dev/disk/by-uuid/44D7-133E does not exist 
```

It looks like we found the culprit, can you show me what I would change in /etc/fstab to make it work without wiping out all of Ubuntu's default settings?

Thanks again,

Megaqwerty

---

### Post by taurus on 2007-03-21
I recommend you change the UUID back to actual device name for /dev/sda1, /dev/sda2, & /dev/sda5 in /etc/fstab.

```

# /dev/sda1
/dev/sda1   /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda2
/dev/sda2   /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
/dev/sda5   /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1

```

---

### Post by Megaqwerty on 2007-03-21
Thank you very much for your speedy reply!

The problem has been solved, as per your instructions.

Thanks again,

Megaqwerty

---

