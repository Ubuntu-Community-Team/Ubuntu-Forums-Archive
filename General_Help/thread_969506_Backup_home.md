---
title: "Backup /home"
date: 2008-11-03
forum: General Help
---

### Post by OsamaK on 2008-11-03
I want to reinstall Ubuntu, (because of a complex dependence problem) but before doing that, I want to find a good, easy way to backup and recovery my /home/.

Is there any suggested way?

---

### Post by Coreigh on 2008-11-03
In the past I have simply copied the whole folder, the /home/user folder not all of /home, to a network drive or even a CD-R. I also included copies of customized system files (httpd.conf, samba.conf, xorg.conf & fstab, etc).

However I was not concerned with customized user preferences. I was OK with recreating the user profile. It would be intersting to know how to back-up and restore a profile intact.

---

### Post by ajgreeny on 2008-11-03
Use rsync or if you want a gui, grsync, and backup the whole of your home folder to a usb drive, dvd-r or whatever medium you have.  It works a treat with the defaults of grsync, but it is better if your usb drive, if that is waht you use, is formatted as ext3 or ext2, as it will not throw up the odd error message that a fat32 drive does.

---

### Post by OsamaK on 2008-11-05
Is that including users' profile and settings (I do not want that), just files (Video, Documents, and other folders) of all users on the machine.

---

