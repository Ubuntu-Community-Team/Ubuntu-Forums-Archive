---
title: "[SOLVED] Mount help"
date: 2008-08-23
forum: General Help
---

### Post by JacksonCash on 2008-08-23
I'm a complete beginner. A friend of mine helped me set up my ubuntu partition a little over a month ago. For various reasons, I ended up re-doing the whole thing. 

Anyway, I know the commands I need to mount the windows drive, but I get told:
```
mount: can't find /dev/sda2 in /etc/fstab or /etc/mtab
```
So, I need to add something like:
```
/dev/sda2 /dev/sda2 vfat defaults 0 0
```
to my fstab. This is where problems arise. fstab doesn't let me save any changes. If anyone can help with that, I'd be really greatful. 

Also, he did something that he said would mean I wouldn't have to re-mount the drive every time I start up, any info on that would be good too.

Thanks in advance.

---

### Post by BTMark on 2008-08-23
If fstab isn't letting you save any changes, are you sure that you are opening it as root? Open up a terminal, and type in: ```
sudo gedit /etc/fstab
```
 
That should be able to let you save your changes.

---

### Post by livestockPimp on 2008-08-23
/dev/sda2 /dev/sda2 vfat defaults 0 0

This is incorrect since the mount point and the device are the same.

if you want to mount your Windows drive onto lets say /mnt/windows then the command you could add this to the fstab for mounting on boot.

/dev/sda2 /mnt/windows vfat defaults 0 0

if you wanted to mount it as a once off or only occasionally then you would type from the # prompt:

mount /dev/sda2 /mnt/windows -t vfat

This is of course providing that your windows partition is formatted with a FAT filesystem and not NTFS.

---

### Post by JacksonCash on 2008-08-23
:KS
Stars all around, thanks guys!

---

### Post by JacksonCash on 2008-08-23
As an aside... what would I do if the filesystem were NTFS?

---

### Post by BTMark on 2008-08-23
JacksonCash, there's a lot of great guides to mounting NTFS, [_this_]("http://ubuntuforums.org/showpost.php?p=5013204&postcount=1") seems to suit the need of automounting NTFS pretty well. Hope this helps.

---

