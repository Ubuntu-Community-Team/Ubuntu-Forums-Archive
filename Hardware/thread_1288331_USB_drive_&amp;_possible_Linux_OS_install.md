---
title: "USB drive &amp; possible Linux OS install"
date: 2009-10-11
forum: Hardware
---

### Post by texas.chef94 on 2009-10-11
The attachment is merely to show its presence and condition. However when I go to nautilus I see no proof of it being recognized.
Either point me to article or detail steps to format drive, mount, permission etc.
Thanking you again for your assistance

---

### Post by Arup on 2009-10-11
> **texas.chef94 said:**
> The attachment is merely to show its presence and condition. However when I go to nautilus I see no proof of it being recognized.
Either point me to article or detail steps to format drive, mount, permission etc.
Thanking you again for your assistance

You need to format it with Gparted for nautilus to recognize it.

---

### Post by texas.chef94 on 2009-10-11
> **Arup said:**
> You need to format it with Gparted for nautilus to recognize it.

Thank you will do. Now can you point me to mount, permission, etc

---

### Post by atomizer on 2009-10-11
You should format it as FAT32 to recognise it on all hardware (FAT32 is the standard for USB drives)
Mounting will be automaticly if you have formatted the drive.
About permissions I am not shure, but I believe that on the FAT32 filesystem there are no permissions needed/possible and everything will be writable/readable by all

---

### Post by Arup on 2009-10-11
> **texas.chef94 said:**
> Thank you will do. Now can you point me to mount, permission, etc

Provided you have enabled medibuntu repositories, do a sudo apt-get install pysdm its a gui for mounting and setting permissions.

---

