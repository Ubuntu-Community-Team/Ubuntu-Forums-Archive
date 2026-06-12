---
title: "2 Hard Drives: 1 formatted"
date: 2007-10-10
forum: Hardware &amp; Laptops
---

### Post by messagesend on 2007-10-10
Im running Kubuntu right now. I just put in an extra hard drive for backing up all my files to, so I can install windows (certain programs require) and then Ubuntu together. I hear it must be done in that order.

Does anyone know how I might access the new drive? The application QTParted successfully found and formatted it. It showed up as /dev/hdb. The only partition being /dev/hdb1. The file system is now ext3.

I have tried navigating in Konqueror to /dev/hdb and /dev/hdb1. It makes no difference if i type /dev/cheesemellons. i just see blank space, and the address bar appends 'locate:'  

example: "locate:/dev/cheesemellons". navigating to /dev i see both hdb and hdb1. it just asks what program to open them with. selecting Konqueror just causes the same thing to happen again, which is delightful.  they look like 3 blocks with big padlocks on them.

I found other posts concerning multiple hard drives for multiple OS installations. I simply want to back up my files. Can anyone help?
Your expertise is or possibly are appreciated.

---

### Post by gautada on 2007-10-10
You have to mount the drive to make it visible.

```
%>sudo mkdir /mnt/newdrive
%>sudo mount /dev/hdb1 /mnt/newdrive
```

This will make the new drive available at /mnt/newdrive.  Of course you can change that for your preferences.

---

### Post by messagesend on 2007-10-10
Thanks for that gautada.
Do the commands require the " %> "
It wouldnt do anything until I removed those. I can now access the drive and I see there a 'locked' Lost + Found folder. It still will not allow me to write anything to the disk however. I recieve 'Access Denied'.

---

### Post by FITorion on 2007-10-10
chown -- help

that should tell you what you need to know to change the drives owner from root to your user name.

I just had to do this but don't remember all the details chown --help should get you what you need to know.

---

### Post by messagesend on 2007-10-11
you are exactly right there. the full solution can be found at:
[http://ubuntuforums.org/showthread.php?t=572613](http://ubuntuforums.org/showthread.php?t=572613)
thanks for your help

---

