---
title: "formatting a usb hard drive"
date: 2008-08-28
forum: General Help
---

### Post by rdpsycho on 2008-08-28
hello i am trying to format a usb hard drive to fat32 so i can use it with my ps3, i have gparted installed but when i try to use it the option to format from right clicking on the drive is grayed out. there is also a lock icon on all the drives. what do i do?

---

### Post by Crafty Kisses on 2008-08-28
Does the USB drive show up, post the results of > lsusb

---

### Post by rdpsycho on 2008-08-28
clinton@clinton-desktop:~$ lsusb
Bus 002 Device 006: ID 0caf:2339 Buslink 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 1532:0101  
Bus 001 Device 004: ID 046d:c222 Logitech, Inc. 
Bus 001 Device 003: ID 046d:c221 Logitech, Inc. 
Bus 001 Device 002: ID 046d:c223 Logitech, Inc. 
Bus 001 Device 001: ID 0000:0000  

buslink is my drive and yes it works fine, i started gparted by using sudo gparted in the terminal

---

### Post by LateNiteTV on 2008-08-28
try this:
```
mkfs -t vfat /path/to/device
```

---

### Post by rdpsycho on 2008-08-28
nevermind i found the answer in another topic, all i had to do was unmount the drive before starting gparted

---

