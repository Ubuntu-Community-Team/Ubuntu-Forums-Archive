---
title: "windows hard drive won't stay mounted"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by screams on 2007-01-21
i mounted my windows hard drive so i could access the files on it and save files from ubuntu to it... but i can't see anything in it when i open it up because i don't have permissions to do anything to it. i tried rebooting to see if that fixed the problem, but when i logged back into ubuntu it was no longer mounted.

---

### Post by taurus on 2007-01-21
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by screams on 2007-01-21
thanks. i have it mounted now, and i can actually see the files and folders on the windows drive... but i still don't have the permissions to write or execute files on it. i can't change the permissions by right clicking and selecting properties>permissions either... because i don't have permissions to change the permissions...

---

### Post by taurus on 2007-01-21
If it's an ntfs filesystem, you cannot write to it UNLESS you install ntfs-3g first.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

---

### Post by screams on 2007-01-21
ok. i didn't know that ntfs partitions did that. i just reformatted at made it a fat partition instead. thanks for the help.

---

