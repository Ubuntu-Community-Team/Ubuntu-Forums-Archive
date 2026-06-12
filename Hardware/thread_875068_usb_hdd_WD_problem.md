---
title: "usb hdd WD problem"
date: 2008-07-30
forum: Hardware
---

### Post by eldersoares on 2008-07-30
hi!
i have a usb hard disk WD Passport with 160gb of space and it always worked very fine. but now i'm using ubuntu with 2 different users and the hdd was always mounted just for the first user to make logon and the others couldn't access due to permissions problems.

so i decided to add a line in /etc/fstab to mount it before starting gnome. but now the problem is that i can't unmount it! it tells it was not mounted by hal, or i don't have enough permissions or just that it is not mounted.

here's the line i added in fstab:

/dev/sdb1 /media/WDPassport vfat rw,noexec,nosuid,nodev,iocharset=utf8,uhelper=hal,uid=1000,umask=000 0 0

i have ubuntu hardy in a dell inspiron 6400 laptop 


thanks!

---

### Post by ajgreeny on 2008-07-30
The command ```
sudo umount /dev/sdb1
``` in terminal should work.

---

### Post by eldersoares on 2008-08-01
thanks but i need to find a way to unmount without using the terminal because this laptop is used by people who doesn't know how to use the terminal and want to use ubuntu 100% in a visual way

---

### Post by mc4man on 2008-08-01
I'm not sure now with the fstab entry (maybe comment/delete it) but you (as first user) should be able to take care of what you wanted in system -> authorizations -> storage.
Try granting your other user(s) explicit authorization to mount filesystems from removable drives (you can set remember authentication or not).

What's also handy is to give yourself (or others) explicit to unmount filesystems mounted by others (root is included as other)

If you have other partitions/drives look at mount file systems from internal drives  (for those not mounted at boot. A simple d.click on icon to mount, r.click to unmount, full rw permissions)

---

### Post by ajgreeny on 2008-08-01
I think mc4man is right to be uncertain about things now you have added the line to fstab.  I think you will either need to use the terminal to unmount in the way I said, or comment out the fstab line and then use the panel applet Disk Mounter.  That lets you click on an icon to mount or unmount a disk with ease, though it may still need a password to do it, I'm afraid, for anyone other than the first admin user, unless you also give the other users admin rights.

---

### Post by eldersoares on 2008-08-03
thanks for the answer, i didn't know the 'authorizations' tool. it was parcially solved: now any user can mount and unmount but only the first user that mounted have rw permissions. even if i unmount and mount again, the second user still can't write data.

---

