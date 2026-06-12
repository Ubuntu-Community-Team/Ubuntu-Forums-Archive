---
title: "Two Identical SD cards on external reader one works the other doesn't"
date: 2008-10-14
forum: Hardware
---

### Post by american.swan on 2008-10-14
I messed up.  I changed some setting and ruined my working system.  

Few hopefully easy to fix problems.

1.  Two 4gig sd cards.  They **used to** both work perfectly in my card reader.  I messed up the mounting settings on one so now only one mounts correctly.  The other refuses to mount.  How can I get it mounting correctly again.

2.  After windows has manipulated the data on one of the cards, Ubuntu locks the files like I'm not the owner.  How can I quickly make [username] owner of /media/disk

Thanks.

---

### Post by american.swan on 2008-10-14
I fixed number 1 by using the "information" from "partition editor" to get me the /dev address then I used fstab to mount the address to media/disk with "auto" as the filesystem

---

### Post by american.swan on 2008-10-14
I still have permissions issues.

I tried chown on /media/disk.  I tried -R and it refused to change the permissions for me.

---

### Post by american.swan on 2008-10-14
By changing chown now I have to manually mount and umount with sudo.  It won't let me do it from the desktop.

This is rather annoying to say the least.

---

### Post by american.swan on 2008-10-14
I would like to direct anyone interested to the following excellent post on fstab that helped me fix the last of my problems.

[http://ubuntuforums.org/showpost.php?p=1653968&postcount=1](http://ubuntuforums.org/showpost.php?p=1653968&postcount=1)

---

