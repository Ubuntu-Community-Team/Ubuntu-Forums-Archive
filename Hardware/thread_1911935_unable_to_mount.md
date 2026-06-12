---
title: "unable to mount"
date: 2012-01-19
forum: Hardware
---

### Post by new to linux help needed on 2012-01-19
whenever i try to open my usb flash drive i get this 

Unable to mount lexar
Error creating moint point: Read-only file system [IMG]http://ubuntuforums.org/attachment.php?attachmentid=211139&stc=1&d=1327010361[/IMG]

---

### Post by ajgreeny on 2012-01-19
More info please.


[LIST=1]
[*]What format is the USB drive, fat32, ext#, etc etc?
[*]Is there an entry for it in /etc/fstab?  (USB drives do not normally need a fstab entry.)
[*]Is the partition on it labelled, ie named "lexar" so that it should mount at /media/lexar folder?
[/LIST]

---

### Post by new to linux help needed on 2012-01-19
should be fat 32 but it was screwed up and i dont know what happened....

---

### Post by SteveDee on 2012-01-20
> **new to linux help needed said:**
> should be fat 32 but it was screwed up and i dont know what happened....

...then you probably need to run GParted and consider re-formatting it.

---

