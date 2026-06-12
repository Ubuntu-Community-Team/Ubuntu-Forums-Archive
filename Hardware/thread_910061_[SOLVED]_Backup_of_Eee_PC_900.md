---
title: "[SOLVED] Backup of Eee PC 900"
date: 2008-09-04
forum: Hardware
---

### Post by AlanRogers on 2008-09-04
Fellow Ubuntans

I've successfully made a USB boot stick with eeebuntu NBR on it and, subject to further testing, I'm very happy.

When it comes time to install eeebuntu properly, is there an easy way to backup the existing discs to images, so that I can restore these if it all goes wrong?

Thanks in advance

---

### Post by AlanRogers on 2008-09-04
I was able to do this using a 4GB UFD and```
sudo dd if=/dev/sda1 of=/media/usbdrive/sda1.img
sudo dd if=/dev/sda2 of=/media/usbdrive/sda2.img
```
I was very surprised that the 4GB section compressed to 2½ and the 16GB to 1½ - I was expecting roughly equal sizes and didn't have removable media to deal with that.
 
For new users reading this post, I am no expert, just willing to have a go. The dd utility is very powerful, for which read dangerous. If you're not absolutely certain what you're doing, do lots of reading first. There are absolutely no 'Are you sure?' warnings before you overwrite important stuff!

---

