---
title: "Reading Chinese/Japanese filenames in Ubuntu Server"
date: 2008-08-20
forum: General Help
---

### Post by digitalsky on 2008-08-20
Hi all,

I'm looking for some help on displaying chinese/japanese files/folders in my ubuntu server 8.04 LTS.

What I've done is I got an ntfs external hdd that I used to attache to an XP computer.  With that I've created some files/folders with Chinese/Japanese characters.  I have since moved the drive and it is now connected (by usb) to my ubuntu server.  I've mounted the drive by:

```
mount -t ntfs -o nls=utf8 /dev/sdb1 /mnt/exthdd
```

I also set up samba to share the /mnt/exthdd directory.  From Vista/XP, I can mount /mnt/exthdd and can see all characters normally.  However, when I use the console (CLI) in ubuntu or when I ssh over to ubuntu using putty in Windows, the characters show up as "ãã«ãç¾é¢¨ä¼".  

I did something similar before with ubuntu desktop and I remember I was pleasantly surprised that it could see all the asian chars in CLI.  Does anyone know how I can get Ubuntu Server to do the same?

BTW my locale setting is: 
```
# locale
LANG=en_CA.UTF-8
LC_CTYPE="en_CA.UTF-8"
LC_NUMERIC="en_CA.UTF-8"
LC_TIME="en_CA.UTF-8"
LC_COLLATE="en_CA.UTF-8"
LC_MONETARY="en_CA.UTF-8"
LC_MESSAGES="en_CA.UTF-8"
LC_PAPER="en_CA.UTF-8"
LC_NAME="en_CA.UTF-8"
LC_ADDRESS="en_CA.UTF-8"
LC_TELEPHONE="en_CA.UTF-8"
LC_MEASUREMENT="en_CA.UTF-8"
LC_IDENTIFICATION="en_CA.UTF-8"
LC_ALL=
```

Thanks in advnace for your help.

---

### Post by digitalsky on 2008-08-22
Anyone please?

---

### Post by Brian Lee on 2008-09-01
I have the same problem/request too.. BTW how did you manage to show Chinese character on CLI over desktop version?

---

### Post by digitalsky on 2008-09-01
I didn't have to do anything for the desktop version. It just worked on a fresh ubuntu install.

---

### Post by mellowd on 2008-09-01
Have you set the right alphabet codes in putty?

---

### Post by digitalsky on 2008-09-01
Yes I've done that and the fonts displayed properly.  But I was able to display chinese/japanese even on the server itself (ie. in the command line, not from another computer)

---

