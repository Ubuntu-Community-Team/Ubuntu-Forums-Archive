---
title: "Brother DCP115c on ubuntu 6.10 HELP"
date: 2007-04-02
forum: Hardware &amp; Laptops
---

### Post by Bwakas on 2007-04-02
Hello
 Ubuntu newbie here- Ihave run into problems with my new Brother DCP115c - I have followed instructions on installing the alternate solution to drivers for this printer on linux namely mfc210. However after installing the drivers lpr and cupswrapper it appears i am no where near getting the printer to work . Trouble is there were no errors reported during install - when i try to print i get the message that the item has been sent to the printer then nothing the 
 /var/log/cups/error log shows:
> 
E [02/Apr/2007:12:11:53 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:12:11:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:11:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:11:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:04 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:12:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:12:13:21 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:12:13:28 +0100] [Job 42] No %%BoundingBox: comment in header!
E [02/Apr/2007:12:29:25 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Apr/2007:12:31:53 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:12:32:10 +0100] [Job 43] No %%BoundingBox: comment in header!
E [02/Apr/2007:12:32:39 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Apr/2007:14:32:54 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:14:34:56 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:14:37:58 +0100] [Job 44] No %%BoundingBox: comment in header!
E [02/Apr/2007:14:38:34 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:14:38:41 +0100] [Job 45] No %%BoundingBox: comment in header!
E [02/Apr/2007:15:10:49 +0100] Creating missing directory "/var/run/cups/certs"
E [02/Apr/2007:15:37:01 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Apr/2007:15:52:43 +0100] Creating missing directory "/var/run/cups/certs"
E [02/Apr/2007:16:35:33 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:16:49:20 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:16:50:16 +0100] [Job 47] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:50:54 +0100] [Job 48] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:51:21 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:16:51:21 +0100] [Job 48] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:51:21 +0100] PID 8368 (/usr/lib/cups/backend/usb) crashed on signal 9!
E [02/Apr/2007:16:51:30 +0100] [Job 49] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:51:45 +0100] [Job 50] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:51:48 +0100] [Job 51] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:53:33 +0100] CUPS-Delete-Printer: Unauthorized
E [02/Apr/2007:16:55:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:39 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:44 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:44 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:49 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:49 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:54 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:54 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:58 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:16:55:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:55:59 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:02 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:08 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:09 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:14 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:14 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:14 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:16 +0100] [Job 52] No %%BoundingBox: comment in header!
E [02/Apr/2007:16:56:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:19 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:24 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:24 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:24 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:29 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:16:56:34 +0100] cupsdAuthorize: Local authentication certificate not found!
E [02/Apr/2007:21:15:32 +0100] [Job 53] No %%BoundingBox: comment in header!
E [02/Apr/2007:22:18:20 +0100] [Job 55] No %%BoundingBox: comment in header!
E [02/Apr/2007:22:53:12 +0100] CUPS-Add-Modify-Printer: Unauthorized
E [02/Apr/2007:22:53:19 +0100] [Job 56] No %%BoundingBox: comment in header!


PLz helpi do not want to return to windows tho as this is the third device i am having trouble with it is looking more likely!

---

### Post by rldsoftware on 2007-08-24
I don´t know if you have solved the problem yet, but if you have can you post it on the board, and/or mail it to me (robinvanleeuwen@gmail.com). If you haven't solved the problem yet, don't worry, you won't have to switch back to Windows.

A first solution to the problem is to use the "HL1250" driver that comes with Ubuntu, that works fine for the common print jobs ( i don't know what the difference would be with the HL2030 driver and the HL1250 driver, haven't check it yet).

But i have installed Ubuntu in all kinds of different flavors 6.10 to, and i always managed to get the official driver working. I remember the biggest work-around which should not be needed was to install a chroot with the x86 version (i use amd64) and print it trough that way. I had it solved by way other simpeler solutions too.

Oops, i just read in the subject that you are talking about the DCP115c driver, and not the HL2030 driver, but i guess the same applies, and i won't delete the above post for other people with problems with official Brother drivers and CUPS.

Kind regard and have fun,

Robin van Leeuwen

---

### Post by rldsoftware on 2007-08-24
To update my message to you problem (maybe): When you install a printer under GNOME it suggest a driver for your printer. In my case the HL1250 driver instead of the HL2030 driver that is not in the standard database. I guess the same thing applies with the DCP115c. 

If you don't have GNOME but use kubuntu you can always apt-get gnome and remove it afterwards, altough i like having both on my desktop, since KDE gives a lot more flexibility (to my taste) and GNOME is a lot more, sorry i don't know the english word for it but the Dutch word is 'overzichtelijk' maybe someone can translate. It means GNOME give me a better/and simpeler/cleander  overiew of installed and often used applications. GNOME looks more tidy than KDE , and KDE a bit more sloppy, IMHO, but that's way of the subject of this thread so i'll stop now.... :-)

Kind regards and have fun,

Robin van Leeuwen
RLD Software

[email]robinvanleeuwen@gmail.com[/email]

---

