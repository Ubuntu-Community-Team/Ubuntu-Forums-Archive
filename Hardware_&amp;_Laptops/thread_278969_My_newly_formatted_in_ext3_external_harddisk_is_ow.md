---
title: "My newly formatted in ext3 external harddisk is owned by root"
date: 2006-10-17
forum: Hardware &amp; Laptops
---

### Post by mostwanted on 2006-10-17
How do I make it readable and writeable by everyone every time it is plugged in?

Right now it is auto-mounted to /media/usbdisk

[COLOR="Navy"]**Update: Never mind, it was simpler than I thought! Just chowned and chmoded the folder. I thought it would only last until next remount, but I was wrong.**[/COLOR]

---

### Post by hopstah on 2006-10-17
by everyone?  or just by one user?

to make it readable by everyone, make sure that every user that you want to give access to is under a certain group - let's just say the 'user' group.  then perform these commands:```
chmod 775 -R /media/usbdisk/
chgrp user -R /media/usbdisk
```
the first command makes the drive readable and writeable to both the owner and anybody in the group.  the owner of the drive will stay 'root' but the second command changes the group to the 'user' group, and will give read and write access to any user who is also in the 'user' group.

note:  this only works on drives which support linux permissions, so this wouldn't work on a fat32 drive.  just so you know.

i hope this helps you out.

note:  read the whole post before typing a response.  i just now saw your update...... sigh

---

