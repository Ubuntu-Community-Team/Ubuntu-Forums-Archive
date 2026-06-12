---
title: "Floppy problems"
date: 2005-09-01
forum: Hardware &amp; Laptops
---

### Post by OtubrabNad on 2005-09-01
Any disk that I insert into the floppy contains only read-only files. I'm given the option to run or display files (they're rtf) if I double click them. Choosing display opens them as read-only and clicking run does nothing. Also, I can't seem to save anything to the floppy drive. I right-clicked one of the files, went to properties and then permissions. Read, Write, and Executable were selected under Owner, but only Read, and Executable are selected under Group and Others. I'm not able to change any of these settings because according to the bottom of the screen "You are not the owner so you can't change the permissions." Any suggestions on how to switch my floppy from a read-only drive?

---

### Post by Shen on 2005-09-01
Because of the way Unix permissions work, you can only change the permissions of files that you own; so become the owner before changing the permissions.

Open a terminal, and cd to where drives are mounted (usually "/media"):
```
cd /media
```

Become root (the owner) and create the drive writable:
```
 sudo chmod 777 floppy 
```
You will have to enter your password for the sudo.

Alternatively, are you sure that the write-enable switch physically on the floppy is closed?

---

### Post by OtubrabNad on 2005-09-02
I entered what you suggested in the terminal and I think it unmounted my floppy drive. I tested out the drive and I recieved a "Unable to mount selected drive" message.

---

