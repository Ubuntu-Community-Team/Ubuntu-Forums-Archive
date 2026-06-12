---
title: "Installed with latest Wubi - First boot goes to some command prompt. Where is X11?"
date: 2008-07-22
forum: General Help
---

### Post by DaveBG on 2008-07-22
I just installed latest Wubi-8.04.1-rev506 and ubuntu-8.04.1-desktop-i386 but after i choose Ubuntu in boot.ini it goes to some command line thing. I says i can type "Help" and it lists commands but no gui ?

---

### Post by ago on 2008-07-22
> **DaveBG said:**
> I just installed latest Wubi-8.04.1-rev506 and ubuntu-8.04.1-desktop-i386 but after i choose Ubuntu in boot.ini it goes to some command line thing. I says i can type "Help" and it lists commands but no gui ?

Please press esc after selecting "ubuntu" and try the other boot options see if you can get more info on the actual error

---

### Post by AGMaster on 2008-07-22
Im having a very similar problem, Here's my original set up.

I got my computer with vista 64-bit, when i got it i only saw one of the 2 250gb's hd's i payed for, i found out that it was joined together (is that called raid?) anyway i unjoined one of the hd's but not the other so it (i think the bios) reminds me its not properly configured everytime i load up my computer. Even so i now had to good hd's so i installed vista 32-bit on the second hd (and i used it as the standard os because 32 bit is much more compatible and never crashed!)

Yesterday I installed wubi from the 32-bit drive/os (F:) onto the drive with the 64-bit (C:) and all worked fine for the first 3 boots (of ubuntu), now when i load windows it gives me Windows Vista 32-Bit, Windows Vista 64-Bit and Ubuntu options in windows boot manager (I renamed the vistas with a program i've got).

When I load vista 32 it tells me winload.exe is missing and i need the installation cd to repair, ubuntu load up grub but not ubuntu, i press escape and it gives me a couple of .list files i can load up or reboot, halt, or command line. None of the .list files are found even though I can find them with windows explorer on 64-bit, so i have to reboot and im using my 64-bit to write this message.

Also a couple of hours ago, after ubuntu stopped working i loaded up 32 bit and it checked (CHKDSK) drive c: for errors

It may just be that since I havn't used the C: drive in ages, its  very fragmented which is annoying ubuntu, which is why im using a proffesional defraging tool right now to defrag it.


Regards,

AGM

---

### Post by ago on 2008-07-22
use chkdsk /r

---

### Post by AGMaster on 2008-07-22
Damn, My bad, Seems like when vista 32-bit decided there was something wrong with C: drive, it also decided to remove most of the files and folders in C:/ubuntu! The whole /disk folder is gone!

Im now reinstalling, I wonder y vista 32 doesnt work?

---

### Post by ago on 2008-07-22
Normally it moves the files in a hidden directory called c:\found.000

---

### Post by DaveBG on 2008-07-27
> **ago said:**
> Please press esc after selecting "ubuntu" and try the other boot options see if you can get more info on the actual error

There is no error it just stops. This time i run it in safe mode to see the problem:

Here is screen sorry for crappy Q i made it with phone.

[IMG]http://img177.imageshack.us/img177/7245/picture29vj4.jpg[/IMG]

---

### Post by ago on 2008-07-29
Is this on a raid?

---

### Post by DaveBG on 2008-07-30
No. I have 3x250 hdds and one 750 hdd. They are all standalone. Ubuntu is installed on a 670GB partition on letter N under windows.

---

### Post by ago on 2008-07-30
What is the output of:

mount -t ntfs /dev/sdb5 /root
cat /proc/partitions

---

### Post by DaveBG on 2008-07-30
Well i uninstalled Wubi, delete all and installed again and now it is working. Wired....
I had previous old version installation which after i formatted windows i abandoned and now i deleted it too. Probably some conflict has occured ... dont know. Now is working as it should. I was able to boot and login and use apps etc...

---

