---
title: "Permanent Mounting?"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by drsmk on 2009-08-07
I have made several partitions and  whenever i reboot i have to mount them all. I know i have to edit /etc/fstab to avoid mounting every time i boot but perhaps i am missing the exact procedure. Plz tell me exact way to add entry into /edit/fstab to avoid mounting partitions again and again.

---

### Post by merlinus on 2009-08-07
You can try this for what you are wanting:

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by drs305 on 2009-08-07
We need to know the partitions and filesystem types. Also your UID and the desired mount points (/media/data, /mnt/music, etc). You can get this information from:
```

sudo blkid
id

```

You can start to read up on fstab with this link:
[http://ubuntuforums.org/showthread.php?&t=283131]("http://ubuntuforums.org/showthread.php?&t=283131")

You can also search for psydm and ntfs-config for tools to help with installation. There is a link to pysdm in my signature line, although that app is fairly old and could use some improvement.

---

### Post by drsmk on 2009-08-07
Thanks for help.

---

