---
title: "Wiped Boot Partition, encripted 7.10 file system"
date: 2008-07-22
forum: General Help
---

### Post by nate010111 on 2008-07-22
HELP!
Sorry for the urgent request but I'm going to get made fun of by my homo windows friends if I can't get my data back by tomorrow.

Main Problem:
I have wiped my boot folder that boots encrypted /, /home and /swap partitions.  I don't remember what instructions I used to set this all up but I think I used LVM or some file system like that.  Also, It was ubuntu 7.10.

Somehow when I updated my other unencrypted 8.04 partition it overwrote my /boot with it's boot files, of course it doesn't work.  To make matters worse I don't remember the last time I updated the encripted ubuntu so I don't know what boot to use.

I know how to copy the new files to the boot, I just don't know where to get the files from.  Thanks all.

---

### Post by nate010111 on 2008-07-22
To clarify, I use a separate boot loader on 2 different hard drives.  I just switch the boot order.  I don't want to get into why, but it needs to say this way.  So I just need one choice for the encrypted boot option on hd(0,0)

Thanks.

---

### Post by nate010111 on 2008-07-28
Bump, anyone please...

---

### Post by uberdonkey5 on 2008-07-30
hi Nate, I think I have done the same. (I was trying to get rid of Dell media direct to get more space for ubuntu). Have you solved the problem?

Basically I had duff copies of ubuntu off the internet which didn't work, and usb copy of ubuntu didn't work. I got 'error 17' when trying to load (I presume grub is missing).

Now, I borrowed a copy of Hardy heron off a friend, and at least now I can get into the computer (just booted from disk). Tonight I back up all my data from windows and ubuntu onto a hard drive (you can access all the data by using the disk in live mode).

Steps I intend are:
1. boot from ubuntu CD
2. back up all data
3. reboot up in windows (vista) and use repair feature to check windows is OK
4. reformat rest of partitions as windows vista(NTDS) and remove so I have one big partition
5. reinstall ubuntu BUT this time with seperate home partition and operating system partition

(PS. many people now seem to be using external hard drives for data, so they just completely reinstall the operating system when something buggers up.)

Basically I am hoping to recreate the grub installer just by reinstalling ubuntu. Sorry i can't be of more help. I am bored of waiting for a reply here myself (I am very impatient). I will tell you what happened and how much I ruined my system even more tomorrow :D

good luck,
Ian

---

### Post by uberdonkey5 on 2008-07-31
realised that can't boot properly without media direct software, even though it is useless on my system. I reinstalled everything (which enabled me to create larger partition for windows). Unfortunately media direct now has TWO copies!! on my drive. Too much hassle to change this. Just gonna accept it and get some work done.

Ian

---

### Post by nate010111 on 2008-08-04
Error 17 is from grub.

My problem is that I cannot access my data because I have an encrypted home file system.  Do you also have the same??  Does anyone out there know how to backup data from a /home on an ENCRYPTED FS.  or restore my /boot so that it asks for my encrypted password at boot like it did before.  Please help anyone.

---

### Post by uberdonkey5 on 2008-08-06
sorry, missed that bit. No - mine was not encrypted

---

