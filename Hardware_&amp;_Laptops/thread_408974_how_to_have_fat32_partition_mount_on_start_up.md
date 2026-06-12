---
title: "how to have fat32 partition mount on start up"
date: 2007-04-14
forum: Hardware &amp; Laptops
---

### Post by JDee on 2007-04-14
I need to have my fat32 partition mount on start up. I did this with my ntfs before partition but i dont know how to do this with fat32. I prettyu new to linuix. Thanks all

---

### Post by amohanty on 2007-04-14
Try adding this to /etc/fstab

/dev/sdc1       /mnt/windows     nfat32    user,auto,umask=007,gid=100 0       1

of course replace sdc1 with your drive spec and replace /mnt/windows with the mount location.

HTH
AM

---

### Post by cantormath on 2007-04-14
You might also what to use NTFS-3g to mount it.  This way you can read and write to the drive.  

Here is a good tutorial
[http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)

---

### Post by shae on 2007-04-14
He does not need to use NTFS-3g to mount it because Ubuntu has fat32 rw support by default.  

/dev/sdc1 /mnt/windows nfat32 user,auto,umask=007,gid=100 0 **0**

So it will not try to check its integrity and complain about the MBR not matching the backup.  At least that happened for me.

---

### Post by amohanty on 2007-04-15
good catch... wonder why that does not happen with me. will have to find out??

---

### Post by taurus on 2007-04-15
> **shae said:**
> 
/dev/sdc1 /mnt/windows [COLOR="DarkRed"]**nfat32**[/COLOR] user,auto,umask=007,gid=100 0 **0**


:confused: 

```
/dev/sdc1   /mnt/windows   **vfat**   user,auto,umask=007,gid=100   0   0
```

---

### Post by amohanty on 2007-04-15
I have to take the blame here. too many typos in my original post.

Sorry.
AM

---

### Post by JTux on 2007-04-15
I have a fat32 partition automatically mounted on startup.

My /etc/fstab/ looks like this 
 
```

/dev/sda8       /media/shared   vfat    defaults,utf8,umask=007,gid=46,           0       1

```

where /dev/sda8 is the fat32 partition and /media/shared is the mount point

---

### Post by JTux on 2007-04-15
> **taurus said:**
> :confused: 

```
/dev/sdc1   /mnt/windows   **vfat**   user,auto,umask=007,gid=100   0   0
```

I noticed that I have a different entry for gid ( gid=46 )

searching for 46 in /etc/group gives 

```
jt69@jt69-laptop:~$ grep 46 /etc/group
plugdev:x:46:haldaemon,jt69

```

---

### Post by cantormath on 2007-04-15
> **shae said:**
> He does not need to use NTFS-3g to mount it because Ubuntu has fat32 rw support by default.  

/dev/sdc1 /mnt/windows nfat32 user,auto,umask=007,gid=100 0 **0**

So it will not try to check its integrity and complain about the MBR not matching the backup.  At least that happened for me.

ah, true, he said fat not ntfs........my  bad....

---

### Post by kro79ece on 2007-04-15
Hey guys, is it possible to make a bootable fat32 partition?
And please a step by step guide would be nice.

---

### Post by MR.UNOWEN on 2007-11-01
Hey can you guys re-explain it again? I'm kinda confused about the whole process. For one thing I can find those exact directories? do we have to create them? A step by step tutorial of what we do in terminal would be appreciated? Also the drive generally shows up in /media, so it would be appreciated if that could stay the same.

---

