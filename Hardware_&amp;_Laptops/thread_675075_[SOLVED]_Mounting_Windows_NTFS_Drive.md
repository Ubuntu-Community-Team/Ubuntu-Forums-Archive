---
title: "[SOLVED] Mounting Windows NTFS Drive"
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by dunk on 2008-01-22
I an unable to mount one of my windows drives. It comes up with the error in the attached file. Has anyone got a work around for this as it has all my MP3s on it. I have tried doing what it says in the script but I can't seem to get it to work. Oh and its only my 2nd day using Ubuntu/Linux. I'm an IT tech, but have only used windows so far.

---

### Post by Daelyn on 2008-01-22
Your NTFS disk has been uncleanly **** down/dismounted, hence you have a flag in it saying "still in use" which ubuntu does not like.

```
 sudo mount -t ntfs-3g /dev/hdd1 /media/<point of your choise> -o force 
```

You will also need to create the mountpoint before this will work with
```
 sudo mkdir /media/<mount point name of your choise> 
```

Hope this helps, mate. Best of luck with linux! :P

---

### Post by dunk on 2008-01-22
God send dude, thanks :)

---

