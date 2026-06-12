---
title: "Mount Error in 8.10"
date: 2008-12-08
forum: Hardware
---

### Post by iceolate on 2008-12-08
I'm not sure what I did, but when I try to mount one of my NTFS drives, I get this error:

[http://i240.photobucket.com/albums/ff111/iceolate3k/mount_error.png](http://i240.photobucket.com/albums/ff111/iceolate3k/mount_error.png)

I think I wanted to change it from Ubuntu's default (instead of it mounting to /media/Local Disk, I wanted it to mount to /mnt/d, for example)

Can someone help me with this? I know how to mount drives in the past, but I never had the installation automatically list them when you go to the Places menu in the panel.

Basically, I want to fix that mount error, change where Ubuntu tries to mount my 3 drives, and automatically do it when I boot up.

Also, I remembered a nice command for the terminal that specifically told me exactly what my drives were and what that their /dev/ place was, however, for the life of me, I cannot find it.

Thank you!

---

### Post by tvtech on 2008-12-08
ls -i /dev/disk/by-uuid

and sudo fsdisk -i

should help

---

### Post by iceolate on 2008-12-08
Aha. This is what I was looking for:

fdisk -l

---

### Post by iceolate on 2008-12-08
Now that I know which drives are which in the /dev, how do I switch what Ubuntu wants to do with them in the Places menu?

---

