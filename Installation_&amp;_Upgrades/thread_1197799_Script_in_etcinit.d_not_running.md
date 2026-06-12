---
title: "Script in /etc/init.d not running"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by bennis on 2009-06-26
So i have a script that i'm trying to run on startup, but it isn't running. I can run it once i'm in ubuntu and it works fine, but for some reason it won't run when it's convenient. I've posted a copy of the script below.

```
umount /media/disk
mount /dev/sdc1 /media/disk-1
mount -o bind /media/disk-1/My\ Documents/My\ Pictures/ /home/ben/Pictures/
mount -o bind /media/disk-1/My\ Documents/My\ Videos/ /home/ben/Videos/
```

---

### Post by master_kernel on 2009-06-26
Did you run '$ update-rc.d foo defaults'? (Where 'foo' is your script name)

---

### Post by bennis on 2009-06-27
I have not. I shall look into this command. Thank you.

---

