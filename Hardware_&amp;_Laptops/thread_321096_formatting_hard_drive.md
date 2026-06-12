---
title: "formatting hard drive"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by Chemist on 2006-12-18
I've installed QTParted and tried to format my second hard drive but it will not keep its file type, ie FAT32 or ext3.

This is what I get when I launch QTParted through the terminal

X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error: Could not detect file system.
Error: Could not detect file system.
- FORMAT /dev/hdb1 ext3
Error: Could not detect file system.
Error: Could not detect file system.
Segmentation fault (core dumped)

I have formatted it then tried to commit the changes but it tells me the file type in unknown.

Does that mean my hard drive is knackered or am I being stupid????

---

### Post by taurus on 2006-12-18
Is /dev/hdb1 currently mounted when you try to format it?  

Applications -> Accessories -> Terminal
```
df -h
```

---

### Post by Chemist on 2006-12-18
sorry should have mentioned that, nah its not mounted

---

### Post by taurus on 2006-12-18
If you want to format your second harddrive, /dev/hdb1, to ext3, you can do it from a terminal in Ubuntu.  No need to even use gparted or QTParted (or any other parted).  Otherwise, try to boot with the LiveCD and use gparted from the LiveCD to convert it to fat32 then...

---

### Post by Chemist on 2006-12-18
managed to format it through the terminal, seems to be working for now

---

