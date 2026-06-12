---
title: "Only root can use my dvd-rw and cd-rw drives."
date: 2005-03-22
forum: Hardware &amp; Laptops
---

### Post by haaglin on 2005-03-22
I was suppose to burn a dvd disc today, but my burning software (K3b)doesn't seem to find my dvd-rw drive or my cd-rw drive. I tried to insert a disc in the drive, but i cant even open the drive with it's button. if i try eject with linux i get: eject: unable to open `/dev/hdd'.
But if i log in as root, everything works fine. This has worked before with my user. can anyone help me with this?

---

### Post by Leif on 2005-04-08
Can you post your /etc/fstab file please ?

---

### Post by sinbad782 on 2005-04-10
You might have to add your user to the cdrom group (and floppy and audio at the same time ) O:) 

The command you need will be something like:

sudo addgroup <username> cdrom audio floppy

---

### Post by IdoMcFly on 2005-04-10
check the group of your writer drive in /dev

mine are in the group "disk" so I have to add myself to the "disk" group (and add user "hal" to disk group in order to get automount to work)
```

$ sudo adduser <you> disk
$ sudo adduser hal disk

```

---

