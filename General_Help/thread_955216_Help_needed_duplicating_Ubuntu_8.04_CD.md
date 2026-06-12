---
title: "Help needed: duplicating Ubuntu 8.04 CD"
date: 2008-10-22
forum: General Help
---

### Post by GyroZee on 2008-10-22
Hi all, I recently got my friend's Ubuntu 8.04 CD.I want to make a duplicate CD of it. I tried extracting the ISO image and burning it, but the CD wasn't bootable. Please tell me how to do it.

---

### Post by shawnrgr on 2008-10-22
Just use any burning software, select "Copy Data CD" and copy it. you don't need a second cdrw drive to copy it, you be asked to swap the cd out for the blank one before it writes.

or you can just burn the iso downloaded from ubuntu

---

### Post by CloudFX on 2008-10-22
Brasero will do it for you.  **Applications > Sound & Video > Brasero Disc Burning**.  For some extra help, press F1 to get the awesome Brasero documentation :).

---

### Post by /////// on 2008-10-22
To make a copy of the cd, dd it with this command:
dd if=/dev/cdrom of=/home/username/Ubuntu804.iso
This will create an image which is an exact copy of the cd, even the boot record which you can use to burn to another cd

---

### Post by steveydoteu on 2008-10-22
> **/////// said:**
> To make a copy of the cd, dd it with this command:
dd if=/dev/cdrom of=/home/username/Ubuntu804.iso
This will create an image which is an exact copy of the cd, even the boot record which you can use to burn to another cd

I think that is overkill a little for this purpose though.

CD/DVD buring tools such as brasero would suffice. Especially *if* GyroZee is new to Ubuntu/Linux.

---

### Post by sethvath on 2008-10-22
Save the file as image and burn image not as data.

---

### Post by GyroZee on 2008-10-22
Thanks Guys !!! your suggestions worked ! finally I was able to create my duplicate CD.
I just extracted the ISO image of the CD using ISOMaker tool(trial version, downloaded from the net), and burned the ISO onto the blank CD. The copy worked perfectly as a bootable CD ! 
:-P

---

