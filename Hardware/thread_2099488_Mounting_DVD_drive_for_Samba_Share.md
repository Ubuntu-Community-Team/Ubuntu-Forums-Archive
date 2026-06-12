---
title: "Mounting DVD drive for Samba Share"
date: 2012-12-29
forum: Hardware
---

### Post by pieman711 on 2012-12-29
I'm sharing my PC resources with my rasberry PI that is set up as a HTPC (using raspbmc). It works well sharing my harddrive but I haven't managed to share  the DVD drive yet. I think the problem is that in 12.10 for some reason mounted drives appear in /media/[user]/ instead of just /media/ and now the CD drive appears to mount with the name of the title rather than as cdrom. 
I was having trouble with sharing seperate partitions/harddrives but I fixed this by editing fstab to make the drives mount in /media/ rather than /media/[user]/ as above. I can't remember the exact problem but i think it was something like "couldn't connect the file has no permissions"
how do I either get the drive to mount as /media/cdrom or create a samba share with the current set up?  
Thanks, any ideas appreciated.

---

