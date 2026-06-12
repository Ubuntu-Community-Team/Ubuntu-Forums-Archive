---
title: "Is there a program for..."
date: 2013-01-14
forum: Hardware
---

### Post by lferg on 2013-01-14
I am on 12.10 and my USB drive is owned by root.  Is there a program that will change the permissions for me? I am a termianl retard. I have done sudo chmod........ I can change for folders in on my actual HDD but not any USB.  These is preventing me from copying files to my USB.  So is there a program that will execute these comands for me.  Linux is proving to be rather difficult.

---

### Post by ahallubuntu on 2013-01-14
Try chown:

```
sudo chown -R USERNAME:USERNAME /media/USBDRIVE
```

where "USERNAME" is your Ubuntu login name/user name.

and "USBDRIVE" is the name of the USB drive when mounted.

---

### Post by tlhIngan on 2013-01-15
> **lferg said:**
> I am on 12.10 and my USB drive is owned by root.  Is there a program that will change the permissions for me?

> **ahallubuntu said:**
> Try chown:

```
sudo chown -R USERNAME:USERNAME /media/USBDRIVE
```

where "USERNAME" is your Ubuntu login name/user name.

and "USBDRIVE" is the name of the USB drive when mounted.

^^^^^^This is the way to do it.
chmod only changes the permissions.
chown changes the actual owner of the file or folder.

---

