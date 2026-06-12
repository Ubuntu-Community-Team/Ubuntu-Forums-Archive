---
title: "Cd Burner wont burn"
date: 2008-12-13
forum: Installation &amp; Upgrades
---

### Post by razzle82 on 2008-12-13
Hi 
Im new to the world of linux, i recently installed ubuntu 8.04. i tried to burn a cd but it didnt work so i dowloaded couple of other software same result. all it does is burn the image on to my hard disk and doesnt allow to burn the cd.
i would like to know is there any specific procedure in order to burn a cd or am i doing something wrong.
thank you

---

### Post by Partyboi2 on 2008-12-13
This will explain how to burn a ubuntu iso to cd
[https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto)

---

### Post by razzle82 on 2008-12-13
Sorry i wasnt really clear, i have burned Ubuntu in iso and installed it already. i was trying to burn a mp3 cd using ubuntu softwares but it didnt let me.
thank you

---

### Post by Partyboi2 on 2008-12-13
what program are you using to burn with?

---

### Post by razzle82 on 2008-12-14
i tried it with brasco, gnome cd/dvd burner and another one i can't remember the name. so far i have the same result with all of them.

---

### Post by oldos2er on 2008-12-14
What do you mean by "it didn't let me"? Do you see any errors, and if so, what are they?

---

### Post by razzle82 on 2008-12-16
so i typed that command and this it what it gave me. i don't think the Cd rom is mounted

faraz@faraz-desktop:~$ vi/etc/fstab
bash: vi/etc/fstab: No such file or directory
faraz@faraz-desktop:~$

---

### Post by chadeldridge on 2008-12-16
Razzle:  I use k3b it is very much like Nero in many ways.  Here is a guide on installing it and configuring it to burn MP3 to CDA withouth any conversion process.

[http://www.overclock.net/faqs/127519-how-burn-mp3-cd-ubuntu-without.html](http://www.overclock.net/faqs/127519-how-burn-mp3-cd-ubuntu-without.html)

---

### Post by foomonster on 2008-12-16
> **razzle82 said:**
> so i typed that command and this it what it gave me. i don't think the Cd rom is mounted

faraz@faraz-desktop:~$ vi/etc/fstab
bash: vi/etc/fstab: No such file or directory
faraz@faraz-desktop:~$

Razzle - Put a space between 'vi' and '/etc/fstab'. vi is the editor, /etc/fstab is the file you're trying to edit.

---

### Post by razzle82 on 2008-12-16
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=8606eff4-964b-4879-9901-d881e313a1ea / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=9b362036-e77f-40a4-a9ba-5bc4d582322c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
~

from the looks of i think it is mounted properly, so what am i doing wrong

---

### Post by Partyboi2 on 2008-12-16
Are you getting any error messages?

---

### Post by razzle82 on 2008-12-18
No CD/DVD writer found.
K3b did not find an optical writing device in your system. Thus, you will not be able to burn CDs or DVDs. However, you can still use other K3b features like audio track extraction or audio transcoding or ISO9660 image creation

thats the error message i got

---

### Post by Partyboi2 on 2008-12-18
Just wondering is your cdrom capable of burning?

---

