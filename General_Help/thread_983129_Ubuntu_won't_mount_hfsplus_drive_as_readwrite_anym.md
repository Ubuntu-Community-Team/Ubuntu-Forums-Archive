---
title: "Ubuntu won't mount hfsplus drive as read/write anymore"
date: 2008-11-15
forum: General Help
---

### Post by macaholic on 2008-11-15
Here's the situation: I have a separate hard drive for osx in my computer, and it is formatted as hfsplus w/ journaling disabled. Up until; about 3 days ago, I was able to mount this drive and have read/write acess to it with the following line added to my /etc/fstab/```
/dev/sda2 /media/mac hfsplus rw,user,auto 0 0 
```
However, now, when it mounts, it mounts as a read-only file system. At first I thought it might be nautilus somehow circumventing fstab's mounting parameters, but, I then set it so it does not automatically mount on boot, logged in without starting Nautilus, and ran ```
sudo mount /dev/sda2
```
Alas, I could still not write to the drive.
Is there anything wrong with my fstab parameters? I'm completely out of ideas at this point, so any help/input anyone could provide would be most appreciated.

---

### Post by macaholic on 2008-11-18
Bump Anyone?

---

