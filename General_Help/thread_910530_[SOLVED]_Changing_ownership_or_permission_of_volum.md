---
title: "[SOLVED] Changing ownership or permission of volume"
date: 2008-09-04
forum: General Help
---

### Post by Ghoztrider on 2008-09-04
Just a quick easy question. I have 51G partition set up on my ubuntu machine. I can get into it and view files, but I can't drop files into it. I want to open up this partition to everyone to read, write and execute. I looked at the properties of this volume and it is owned by root. I am not sure of the command to use to open up this volume. if this was a file or directory I wouldn't be having this problem.

---

### Post by tuxulin on 2008-09-04
create a directory called blah or whatever in you /media or /mnt folder.
you could then put this in your fstab if you know the partition number.
 
/dev/sdb99 /media/blah ext3 auto,user,rw,exec 0 2

Tuxulin

> I looked at the properties of this volume and it is owned by root
after reading again you have it mounted already.... then type in the terminal
sudo chmod 777 mountpoint

---

### Post by kabotage on 2008-09-04
try typing 
```
sudo nautilus
```
and it will grant root priviliges to nautilus, open up in /root with full access to all files/folders

*Take note that running programs with root privileges can be potentially dangerous as there is no protection for the user. Take due care and always understand what you are doing before messing with important files and remember to back up!* 

goodluck!

---

