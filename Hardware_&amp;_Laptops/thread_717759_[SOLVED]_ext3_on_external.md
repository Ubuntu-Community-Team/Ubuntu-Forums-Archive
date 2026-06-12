---
title: "[SOLVED] ext3 on external"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by itix on 2008-03-07
I have an external hard drive (western digital usb powered 5400 rpm 120 Gb red, and pretty as hell :) ). It was deliveres with out of the box fat32 which I wanted to change to ext3 using gparted. The only problem I have is that this folder "lost+found" which I have no permissions to change and which uses up over 1.9 gigabyte of my harddive.

Does anyone know how to get rid of that thing or at least hide it. I have noticed that I have a similar foder on my acer laptop which is ext3. ext2 doesn't solve the problem either.

---

### Post by wednesday allfather on 2008-03-07
> **itix said:**
> I have an external hard drive (western digital usb powered 5400 rpm 120 Gb red, and pretty as hell :) ). It was deliveres with out of the box fat32 which I wanted to change to ext3 using gparted. The only problem I have is that this folder "lost+found" which I have no permissions to change and which uses up over 1.9 gigabyte of my harddive.

Does anyone know how to get rid of that thing or at least hide it. I have noticed that I have a similar foder on my acer laptop which is ext3. ext2 doesn't solve the problem either.

Root probably owns the folder.  Open terminal and enter
```
sudo chown username /media/name_of_disk/lost+found
```

I'm kinda new to the "chown" command, but I am pretty sure that will allow you to access and delete the files.

---

### Post by itix on 2008-03-07
It wanted an extra operands. Is there any -"delete"-ish operand that I can use.

---

### Post by PmDematagoda on 2008-03-07
Actually the lost+found folder is where corrupted files found during a disk check are stored, so it is advisable to not to remove it.

Also, how do you know that the folder really takes up that much space?

---

### Post by itix on 2008-03-07
Gparted says so, and since I'm going to store data there, I'd like to have my disc clean. The corrupted files where most probably the windows-crappy-os-help-since-it-can't-do-the-job-by-itself-files and my music folder that I started copying but aborted since I hadn't formatted the disc.

---

### Post by taurus on 2008-03-07
Where did you mount that new harddrive, mount point?  Assuming you mount it to /media/storage, post the output of this command from a terminal?

```
du -h /media/storage
```
One thing you should know, ext3 will reserve 5% of your total space for root so maybe that is why you think you have some missing space on your new harddrive.

---

### Post by itix on 2008-03-07
```
du: `/media/disk/lost+found': Permission denied
4.0K    /media/disk
```

I just dont want any stupid folders together with my other folders and files. I want nautlius to ignore or hide it or delete it. Preferrably the last since it takes up disk space..

---

### Post by wednesday allfather on 2008-03-07
if you do the chown command, you will be able to delete it.

---

### Post by itix on 2008-03-07
Wow... am I stupid or what? if permission denied => sudo

```
16K     /media/disk/lost+found
20K     /media/disk
```

---

### Post by itix on 2008-03-07
Yeah, that's great, but it still require an extra operand:
```
chown: missing operand after 'media/disk/lost+found'
```

---

### Post by taurus on 2008-03-07
> **itix said:**
> Wow... am I stupid or what? if permission denied => sudo

```
16K     /media/disk/lost+found
20K     /media/disk
```

See, any missing space!

```
cd /media/disk
sudo rmdir "lost+found"
```
If you really want to remove it.

---

### Post by itix on 2008-03-07
Thanx. For some reason the disk analyzer and gparted see the used-space-amount differently because the disk analyzer told me that 5.5 gig was used which would be equivalent to the 5% that you said earlier.

---

### Post by itix on 2008-03-07
Ok, any idea why I don't have permission to write on the disk?

---

### Post by taurus on 2008-03-07
Yip.  5% of the disk is reserved as a default for root when you use ext3 filesystem.  However, there is an option to run it off so it won't reserve any space at all for that partition.

---

### Post by taurus on 2008-03-07
> **itix said:**
> Ok, any idea why I don't have permission to write on the disk?

If you want to write to /media/disk without using sudo/gksudo, you just need to change the ownership of /media/disk from root to your login name.  

_Assuming_ your login name is **itix**, run

```
sudo chown -R **itix**:**itix** /media/disk
ls -la /media
```

You should be all set now.

---

### Post by itix on 2008-03-07
Thanx again!
That option seemed tempting since I'm going to use it for both my acer and the Eee-pc I've ordered.

---

