---
title: "Seagate ST336607LW - urgent"
date: 2008-09-29
forum: Hardware
---

### Post by joomlamz on 2008-09-29
hello i need help here
how can resolv that problems i have hdd scsi i run live cd ubunto i see hdd  
Mode SEAGATE ST336607LW
SIZE 1019.76MB
PATH /dev/sda
REAL PATH /dev/sda

disklabeltype unrecognized
heads 255
sector/track 63
cylinders 130
total sectors 2088450

i need mount that hdd i try mount /dev/sda cant mount 
i need my information

---

### Post by anystupidname on 2008-09-29
Your question is a little cryptic. I'm gathering you are having difficulty mounting a partition in the liveCD to access/edit files on it?!?

> sudo mkdir /mnt/boob
sudo mount /dev/sda1 /mnt/boob
(if it complains that it doesn't know what file system to use)
> sudo mount -t blah /dev/sda1 /mnt/boob

don't be shy about:
> man mount

---

### Post by mike1234 on 2008-09-29
> **joomlamz said:**
> hello i need help here
how can resolv that problems i have hdd scsi i run live cd ubunto i see hdd  
Mode SEAGATE ST336607LW
SIZE 1019.76MB
PATH /dev/sda
REAL PATH /dev/sda

disklabeltype unrecognized
heads 255
sector/track 63
cylinders 130
total sectors 2088450

i need mount that hdd i try mount /dev/sda cant mount 
i need my information

[B]Are you running live cd now?

M.
[/B]

---

### Post by joomlamz on 2008-09-29
yes i run live cd ubuntu
the disc has windows 2000 server so that no more boots so I used live cd to recover the information


i try to do that....she not work

```
Your question is a little cryptic. I'm gathering you are having difficulty mounting a partition in the liveCD to access/edit files on it?!?

Quote:
sudo mkdir /mnt/boob
sudo mount /dev/sda1 /mnt/boob
(if it complains that it doesn't know what file system to use)
Quote:
sudo mount -t blah /dev/sda1 /mnt/boob
don't be shy about:
Quote:
man mount 
```

---

### Post by mike1234 on 2008-09-29
yes i run live cd ubuntu
the disc has windows 2000 server so that no more boots so I used live cd to recover the information

Are you trying to recover data from Windows 2000 (your hard drive), or repair it? Why not just put your Win 2000 disk in and repair it? 

M.

---

### Post by joomlamz on 2008-09-29
yes i try 
but in windows device manager shows .. more when I try to make reparation may not show the disc ... linux livecd shows more says unallocated 

how can resolv that problems..
i try getdataback o dont see hdd..

---

### Post by joomlamz on 2008-09-29
CAN SEE PRINT SCREEN

[CENTER][IMG]http://i276.photobucket.com/albums/kk39/apllic/Screenshot.png[/IMG][/CENTER]

---

### Post by anystupidname on 2008-09-29
"she not work" doesn't mean anything to me. How did my instructions not work specifically?!?

---

### Post by mike1234 on 2008-09-29
Can you go to "places" and scroll down , click on your hard drive? Forget about gparted if you're trying to access your hard disk.

M.

---

### Post by joomlamz on 2008-09-29
ubuntu@ubuntu:~$ sudo mkdir /mnt/boob
mkdir: cannot create directory `/mnt/boob': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda/mnt/boob
mount: can't find /dev/sda/mnt/boob in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$

can see now what iam say

---

### Post by anystupidname on 2008-09-29
> **joomlamz said:**
> ubuntu@ubuntu:~$ sudo mkdir /mnt/boob
mkdir: cannot create directory `/mnt/boob': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda/mnt/boob
mount: can't find /dev/sda/mnt/boob in /etc/fstab or /etc/mtab
ubuntu@ubuntu:~$

can see now what iam say

you made 2 mistakes:
1) there is a space between /dev/sda1              AND                /mnt/boob
2) there is a 1 (one) after sda...


P.S. 3) if you're interpreting things so literally, the command I originally gave you as a backup option won't work. Now that I know you're dealing with an NTFS file system it would be:

> sudo mount -t ntfs-3g /dev/sda1 /mnt/boob

---

### Post by joomlamz on 2008-09-30
i put that accepted as the code does not show anything
I have to do next

---

### Post by cariboo on 2008-09-30
You won't see anything echoed if you used the command correctly. the next thing to do is to use Nautilus (Places Home Folder) to navigate to where you mounted your hard drive, in the side bar on the left side go File System-->mnt-->boob ,if your hard drive is working the files should show up here. What I suspect from what you have written, is that your hard drive is defective and you may not be able to salvage any data from it.

Jim

---

### Post by joomlamz on 2008-09-30
hey,
Pls. I need a help it´s urgent
I have a HDD running under windows server 2000 (scsi). I can see the hard drive phisically but I can access to my data. I want to recover my data. What should I do? any one can help?

---

### Post by anystupidname on 2008-09-30
Now that you have mounted the drive, you can recover your files... What does the command "mount" all by itself tell you? The last line should show you that /dev/sda1 is mounted. Burn your files to DVD or something?!?

p.s. If the file system on the drive with w2k needs to be fixed, you can use a utility like testdisk but you'll need to install it via apt. (sudo aptitude install testdisk)

---

### Post by joomlamz on 2008-09-30
Anystupidname,
Thank you for your help. But I sent my HDD to South Africa for backup all my data. I had hard time last night.

---

