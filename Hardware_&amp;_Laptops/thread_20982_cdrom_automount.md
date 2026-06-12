---
title: "cdrom automount"
date: 2005-03-19
forum: Hardware &amp; Laptops
---

### Post by IdoMcFly on 2005-03-19
Since an update or since adding a new soundcard, I can't get the desktop cdrom icon anymore : the cdrom doesn't automount aymore.

When plug in an usb key, it does open a nautilus window but no icon on desktop either. :confused: 

Using Hoary Preview.

---

### Post by matid on 2005-03-19
Give output of:
**id hal**

---

### Post by IdoMcFly on 2005-03-19
[QUOTE=matid]Give output of:
**id hal**[/QUOTE]
 thanks for your answer, I've just found out what's going on : all the cdrom /dev entries (hda and hdb for me)  are on "disk" group, and hal is not in the disk group; I added hal to disk and now all is running fine :)

What I don't understand : it did work before "I don't know what" so what's the change to make it broke ?? :confused:

---

