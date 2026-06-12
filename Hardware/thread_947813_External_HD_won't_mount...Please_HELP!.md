---
title: "External HD won't mount...Please HELP!"
date: 2008-10-14
forum: Hardware
---

### Post by twinbreeze on 2008-10-14
My external HD (NTFS) will not mount. it used to mount now all of a sudden it will not.

---

### Post by cariboo on 2008-10-14
Did you happen to unplug the drive while in Windows with out unmounting it properly? If so do what the error messages suggest or boot back into Windows and umount it properly.

Jim

---

### Post by splitlenz on 2008-10-14
Ah 

Well, make sure you remember to hit the "remove drive" button in windows. The hard drive knows if you did or didn't. Luckily you can plug it back into any windows machine and remove it the right way and you can try it again on linux. 

the other thing is, make sure you check your fstab file to make sure it has the correct place to mount it to. for a while, fstab thought my external hard drive was a cdrom. 

i changed it to ```
/dev/sdb1 /media/exthdd auto rw,user,exec,sync 0 0
```

where sdb1 is the external hard drive, exthdd is where to mount to, 
auto is to do it automatically, user is for nonroot, exec so i can run executables, sync to changes take effect immediately.

---

