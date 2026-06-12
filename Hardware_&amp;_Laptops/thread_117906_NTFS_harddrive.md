---
title: "NTFS harddrive"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by Kieffer87 on 2006-01-15
I have a 200GB drive with movies, music, etc that is NTFS. If I go to system, admin, disks. I can access and play all the files. I have it mounted to /Multimedia. However it says permission denied and that only root can access. How do I change this.

---

### Post by amohanty on 2006-01-15
How have you mounted it to /Multimedia ?
If you are doing it via /etc/fstab remember that the **default** option in fourth column means it is mounted as root. Try replacing the ntfs mount line with something like this:
> /dev/sda1       /multimedia        ntfs    ro,user,auto,umask=022        0       0


If you dont understand the above line, post the contents of your /etc/fstab?

HTH
AM

---

### Post by aysiu on 2006-01-15
For a detailed step-by-step, see the fourth link of my signature.

---

### Post by amohanty on 2006-01-15
[QUOTE=aysiu]For a detailed step-by-step, see the fourth link of my signature.[/QUOTE]


I think I will have to plagiarize your sig... a one line answer is sooo much easier :)

---

### Post by Kieffer87 on 2006-01-15
I tryed that but see its a seperate drive not a partition. So when I run that app It doesnt list my drive.

---

### Post by Kieffer87 on 2006-01-15
When I run fstab I dont see it. So I added it but when I try to mount it I get an error that is is busy or already mounted.

---

### Post by Kieffer87 on 2006-01-15
Ok I got it working now, however I copied a file over to my desktop. Now when I try to delete it I get a premission denied error.

---

### Post by amohanty on 2006-01-15
OPen a terminal using Applications->Accessories->Terminal
Type the following and post the output:

> cd Desktop
ls -l filename

Replace filename with the file you copied over.

AM

---

### Post by Kieffer87 on 2006-01-16
Ok my next question. I have read a million posts and I am still a bit confused. I have a 40 gb drive with ubuntu on it that has 19.3GB Free. I also have a 200GB drive with movies, music mostly, and some pictures, etc. I have 99GB free on that. However it is currently NTFS and I want to reformat it to Fat32. Is there a way to make a 99GB partition thats Fat32 and copy the files over and then make the rest of the disk fat32, and make it one big partition? If that makes since. I was gonna copy some files over to my other disk and burn some cds but I figured this may be a bit easier.

---

### Post by amohanty on 2006-01-19
You can do so with something like Partition Magic.

HTH
AM

---

