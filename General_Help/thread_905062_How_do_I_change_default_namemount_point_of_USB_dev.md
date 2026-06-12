---
title: "How do I change default name/mount point of USB device?"
date: 2008-08-29
forum: General Help
---

### Post by Doughy on 2008-08-29
When I plug a USB drive into my machine, it tries to mount it, but fails because I at one time changed the mount point to something like "Doughy's".  I think the apostrophe is screwing it up.

How can I change the default mount point of this device?

---

### Post by cdtech on 2008-08-30
Plugging a USB storage device creates it's own directory within the "/media" directory, dependent on it's label. To create a label on a USB device:
```
sudo e2label /dev/**sdc1** Doughy
```
(the bold would be your USB device, which can be found using "sudo fdisk -l")

Which will give the device the label "Doughy" and mount the device within it's own directory "/media/Doughy" automatically when you remount it.

Hope this helps......

---

