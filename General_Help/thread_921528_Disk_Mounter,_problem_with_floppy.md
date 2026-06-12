---
title: "Disk Mounter, problem with floppy"
date: 2008-09-16
forum: General Help
---

### Post by rakan_dr on 2008-09-16
hi guys. I have a problem with the Disk Mounter app. It shows that i have a floppy drive, but i don't! I checked if the floppy is enabled in the BIOS but i found that i disabled it. So why it shows that there is a floppy drive to mount??? When i try to mount it, it says it can't!

---

### Post by EmanresuusernamE on 2008-09-16
Type in the following command:

ls /dev

If you have any fd* entries in there, Ubuntu/Linux thinks you have floppy drives.

Do you have any smart card, or one of those 6 in 1 readers in your system?  Ubuntu  will detect those, but be unable to mount them if you have no media in them.

---

### Post by rakan_dr on 2008-09-17
> **EmanresuusernamE said:**
> Type in the following command:

ls /dev

If you have any fd* entries in there, Ubuntu/Linux thinks you have floppy drives.

Do you have any smart card, or one of those 6 in 1 readers in your system?  Ubuntu  will detect those, but be unable to mount them if you have no media in them.

Yeah, i found fd in /dev. And yes i have a 6 in 1 reader. So is this the problem??? Why doesn't ubuntu see it as 6 in 1 reader???

---

### Post by EmanresuusernamE on 2008-09-17
Really it should see them as sd* drives.  How are you trying to mount the floppy drive?  Through the GUI, or using the mount command?

---

### Post by rakan_dr on 2008-09-17
> **EmanresuusernamE said:**
> Really it should see them as sd* drives.  How are you trying to mount the floppy drive?  Through the GUI, or using the mount command?

Through the GUI, using Disk Mounter precisely.

---

### Post by EmanresuusernamE on 2008-09-18
Hmmm, have you tried to mount them manually using mount?

Create a directory in /media and then type in:

sudo mount /dev/fd<Number here> /media/<Directory you just created>

What errors do you get?

---

### Post by rakan_dr on 2008-09-22
> **EmanresuusernamE said:**
> Hmmm, have you tried to mount them manually using mount?

Create a directory in /media and then type in:

sudo mount /dev/fd<Number here> /media/<Directory you just created>

What errors do you get?

why did you ask this question? I just want to remove the floppy "which i don't have" from Disk Mounter.

---

### Post by EmanresuusernamE on 2008-09-22
Too see what Ubuntu thinks is there.  If you can mount it, and you don't have a floppy drive, then there could be another issue wrong with your system.

Also, the GUI mounter doesn't always give you the best of error/status messages when mounting drives.  The terminal will...... usually. ;)

---

