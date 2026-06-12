---
title: "Permission denied when trying to write files to removable drive"
date: 2014-12-04
forum: Hardware
---

### Post by geoffmen on 2014-12-04
Using ubuntu gnome 14.04. I can't write files or delete files from a removable device like a USB stick. It says Permission denied. if I open it as root then I can write into it.
There is no fstab entry for the removable device. How can I setup the system so that I don't have to seperately open the device as root in order to write into it?

---

### Post by yancek on 2014-12-04
What is the filesystem type?  Is it a Linux or windows filesystem?  How are you accessing it?  Do you use the file manager under /media/username or some other method?

---

### Post by bilkay on 2014-12-05
Is the device inserted on boot, or do you insert it after you've logged in?

---

