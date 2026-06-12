---
title: "How to format Kingston USB 2.0?"
date: 2008-09-23
forum: Hardware
---

### Post by velickovic on 2008-09-23
Help pls!!!!:(

---

### Post by Crafty Kisses on 2008-09-23
You can format the drive by doing the following, remember the commands will be different, substitute your information:
```
sudo mkfs.ext3 /dev/sda1
```
Once you've done that you have to make the label:
```
sudo e2label /dev/sda1 usb-pen
```

---

### Post by velickovic on 2008-09-23
> **Codename said:**
> You can format the drive by doing the following, remember the commands will be different, substitute your information:
```
sudo mkfs.ext3 /dev/sda1
```
Once you've done that you have to make the label:
```
sudo e2label /dev/sda1 usb-pen
```

Which part in commands should I change??? I'm noob for ubuntu!

---

### Post by Steve1961 on 2008-09-23
> **velickovic said:**
> I install GParted from terminal and can't find it. I'm noob, because I use UBUNTU 3 day only. 	\\:D/

system/Administration/Partition Editor

At least that's where it should be after a sudo apt-get install gparted

---

### Post by velickovic on 2008-09-23
> **Steve1961 said:**
> system/Administration/Partition Editor

At least that's where it should be after a sudo apt-get install gparted

it's there, but i don't see how i can format my USB?

---

### Post by Steve1961 on 2008-09-23
> **velickovic said:**
> it's there, but i don't see how i can format my USB?

Open gparted, use the drop down menu to change to the usb drive, delete existing partitions, and then unmount and remount the usb stick after closing gparted.  Once you've reinerted the usb stick open gparted again and use the drop down menu to move to the drive.  Choose new from the menu and the rest should be self explanatory.

---

### Post by velickovic on 2008-09-23
> **steve1961 said:**
> open gparted, use the drop down menu to change to the usb drive, delete existing partitions, and then unmount and remount the usb stick after closing gparted.  Once you've reinerted the usb stick open gparted again and use the drop down menu to move to the drive.  Choose new from the menu and the rest should be self explanatory.

tnx!!!

---

### Post by Steve1961 on 2008-09-23
> **velickovic said:**
> tnx!!!


You're welcome!

---

