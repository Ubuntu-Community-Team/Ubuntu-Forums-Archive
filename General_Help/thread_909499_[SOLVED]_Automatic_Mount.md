---
title: "[SOLVED] Automatic Mount"
date: 2008-09-03
forum: General Help
---

### Post by CrusaderAD on 2008-09-03
I have a shared folder mounted with my fstab file. Here's the path:

//192.168.5.1/folder1/  /home/user/folder2/  cifs  username=admin,password=password1  0  0

How do I set it so it automatically mounts everytime I reboot?

---

### Post by cdtech on 2008-09-03
What is the output from the command (using your desktop)?
```
smbclient -L //192.168.5.1
```
When prompted for a password just hit [ENTER], apparently you want to mount a share without a password.

The correct format in /etc/fstab should be:
//servername/share /mnt/yourmountdir cifs options 0 0

---

### Post by CrusaderAD on 2008-09-03
I don't really want to post that info here... sorry guy, it's not my network! Isn't there some way to mount the drives while booting up rather than running mount -a everytime?

---

### Post by signifer123 on 2008-09-03
the correct format in fstab, listed above should mount it on bootup if it's available.

---

### Post by CrusaderAD on 2008-09-03
Yeah it does... hmmm not sure why it didn't do it this one time... but it seems to be working now. Thanks

---

