---
title: "Problem with DVD-Ram Reader/Writer on HP 655"
date: 2017-09-11
forum: Hardware
---

### Post by dhira on 2017-09-11
Hi there,
I run Ubuntu LTS 16.04 on HP 655 notebook. DVD device is not reading the information from media anymore. It happened already with Ubuntu 14.04 and now the same with 16.04. There is light if disc ejected/inserted and I can hear disc spinning but no folder or data showed/read.

This is the information with a disc being inserted:
*-cdrom
       Description: DVD-RAM writer
       Product: DVDRAM GT80N
       Producer: hp
       Physical ID: 0.0.0
       Bus-Information: scsi@1:0.0.0
       Logical Name: /dev/sr0
       Version: R102
       Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       Konfiguration: ansiversion=5 status=ready
     *-medium
          Physical ID: 0
          Logical Name: /dev/sr0

Can anybody read if it is hardware or software problem? Any further suggestions if the disc should be calibrated and how (which software)?

I am just an user and I am unfortunately not skilled with hardware or software.

Thanks in advance.

---

### Post by dw1-4 on 2017-09-20
Question is: 

What did it do? 
Did it mount? 
Did you see an icon coming? 
What kind of CD or DVD are you inserting (data, movie)?? 
Did you check in the terminal what happens (or does not happen)?? 
If you report more there is probably a solution. 

When you open a terminal and type mount ENTER, what does it tell about /dev/sr0? Something? Nothing?
Is there an entry in /etc/fstab about /dev/sr0 or is it not telling anything about /dev/sr0?

I suggest: Details please!

---

### Post by dhira on 2017-09-20
It didn't mount. No icon is coming. I tried both CD and DVD, movie, audio and data. I don't know how to check in the terminal except this:
This is the information with a disc being inserted:
*-cdrom
       Description: DVD-RAM writer
       Product: DVDRAM GT80N
       Producer: hp
       Physical ID: 0.0.0
       Bus-Information: scsi@1:0.0.0
       Logical Name: /dev/sr0
       Version: R102
       Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       Konfiguration: ansiversion=5 status=ready
     *-medium
          Physical ID: 0
          Logical Name: /dev/sr0

---

### Post by dw1-4 on 2017-09-20
"I don't know how to check in the terminal": Open a terminal!
You can ask the dash (Standard-Ubuntu)  or look in the menue or try ctrl+alt+T to open one. 
More help in the Ubuntu doc and in the internet!

BTW: What Ubuntu (version, flavour) you have? German?

---

### Post by dhira on 2017-09-22
I run Ubuntu LTS 16.04, German version. I know how to open the terminal, but for what should I specifically search? I also don't know how to read the results that I already got:
*-cdrom
       Description: DVD-RAM writer
       Product: DVDRAM GT80N
       Producer: hp
       Physical ID: 0.0.0
       Bus-Information: scsi@1:0.0.0
       Logical Name: /dev/sr0
       Version: R102
       Fähigkeiten: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       Konfiguration: ansiversion=5 status=ready
     *-medium
          Physical ID: 0
          Logical Name: /dev/sr0

---

### Post by Yellow Pasque on 2017-09-22
Your output does not indicate any issue. Boot a LiveUSB of some sort. If the drive doesn't work in that environment, then it's likely a hardware issue. If the drive does work, then you can start investigating your Ubuntu install.

---

### Post by dw1-4 on 2017-09-23
> **dhira said:**
> I run Ubuntu LTS 16.04, German version. I know how to open the terminal, but for what should I specifically search? I also don't know how to read the results that I already got:
*-cdrom
       Description: DVD-RAM writer

       Logical Name: /dev/sr0

          Logical Name: /dev/sr0

OK, das ist einfach. 
Du mountest es von der CLI (also Terminal) einfach von Hand. 

Standard-Daten-CD einlegen. Oder Ubuntu-DVD, geht auch. Nur bitte keine Audio- oder Video-CD/DVD, die sind anders. 
Eingeben: 
sudo mkdir /mnt/cd2000
sudo mount -t iso9660 /dev/sr0 /mnt/cd2000
ls -latr /mnt/cd2000

und dann im FileManager unter /mnt/cd2000 nachsehen, WAS da ist. 
Leer? Daten? 
Wenn Daten dann Vorgang moeglich und Technik laeuft. Sehr wahrscheinlich. 

Oder Fehler berichten!
Der muesste sofort angezeigt werden (deshalb lieben wir die CLI). Aufnotieren, hier wiedergeben. 
Anschliessend eingeben: dmesg ENTER. Ganz am Schluss koennte noch was zum Problem stehen. Ist da was?


Natuerlich stimmen so die Rechte nicht, nur root darf. Es ist dann aber ganz einfach, die fstab von Hand anzupassen, um den mount nur noch aufrufen zu muessen. Die Zeile kann ich Dir schreiben. 

In 16.04 Ubuntu muesste es fuer die Wechsellaufwerke settings geben, mit denen man den auto-mount abschalten kann. Ob das vielleicht geaendert wurde? Ich sehe mal nach wo das ist, habe jetzt nur XFCE vor mir ;-)
Nachtrag: Settings (Zahnrad) / Informationen / Wechselmedien. 
Dort wird das Verhalten konfiguriert. Gut und sicher ist, fuer alle und jedes Nachfragen / ask einzustellen. 
Ganz bestimmt NICHT angehakt darf sein: "Beim Einlegen von Datentraegern nie nachfragen oder Programme starten" Wenn dort ein Haken ist, ist das Dein Problem. 

Wenn alles geklappt hat, aber sinnlos ist wegen Rechte, bitte eingeben:
sudo umount  /dev/sr0

umount fuer un-mount ist GANZ wichtig, auch bei Sticks u.a. Unter Windows wird das immer ignoriert, irgendwann tauchen wilde Fehler auf. Deshalb. Also bitte nach dem mounten IMMER unmounten. Oder Rechner herunterfahren, dann wird es erzwungen, was aber auch problematisch sein kann. 

Berichte  bitte die Ergebnisse.

---

### Post by mc4man on 2017-09-23
"status=ready" means the drive reports a disc in the drive with no filesystem on it. Typically seen with blank media & audio cds.
Maybe the drive needs cleaning, maybe it's going bad

---

### Post by dw1-4 on 2017-09-23
> **mc4man said:**
> "status=ready" means the drive reports a disc in the drive with no filesystem on it. Typically seen with blank media & audio cds.
Maybe the drive needs cleaning, maybe it's going bad

I assume he can not mount! So he needs to mount manually. 
Since the 80es I have not seen a drive that needed cleaning - try and it will be de-adjusted (aka garbage). 

He shall post the error mesages when he mounts by hand. See my previous post. Most likely it will work fine ;-)
And check the settings in the GUI.

---

### Post by mc4man on 2017-09-23
> **dw1-4 said:**
> I assume he can not mount! So he needs to mount manually. 
Since the 80es I have not seen a drive that needed cleaning - try and it will be de-adjusted (aka garbage). 

He shall post the error mesages when he mounts by hand. See my previous post. Most likely it will work fine ;-)
And check the settings in the GUI.
You only mount a filesystem not a cd/dvd drive. So if no filesystem is detected there is nothing to mount.

---

### Post by dw1-4 on 2017-09-23
if you did not manage to mount something you will never find out if the file system on the cd is valid. Strictly spoken you mount a fs not a device. Actually you do mount a device here: /dev/sr0 is a device, not a fs. This discussion does not help the user to fix a stalled mount process. He shall try to mount the thingie from the CLI and report the issues - it is his issue so we need to respect his needs rather than discussing what exactly is mounted - if it is mounted at all. My 5 cents.

---

### Post by efflandt on 2017-09-25
I thought that different lasers are used for CD vs. DVD since 4.7 GB on a DVD would require a different frequency that up to 700 MB on a CD. For example a standalone DVD player that my boss had stopped reading movie DVD's, but could still read and play music CD's. Or in another case I had an issue with a DVD player no long reading DVD's when the laser lens came loose. Or in the case of an old Sony laptop, its DVD player would apparently overheat and stop reading DVD's after roughly 90 minutes, which would interrupt a 2 hour movie DVD.

If you had some other OS on the computer (like dual booting Windows) you could tell if it was a software or hardware issue. But otherwise if it was working before and is not working now, it might be a hardware issue. I know that I had to order a replacement DVD drive for a friend who I originally bought a Dell laptop for in 2009 and sometime in the past year or two its DVD drive had failed. There is usually a single screw on the bottom of your laptop at the rear of the DVD drive and removing that screw should allow you to remove the DVD drive. Although, you may need to transfer the bracket for that screw on the rear of a replacement drive, along with the faceplate, since replacement drives from other sources (like Amazon) may not include those specifically for your computer. I think other than faceplate and bracket, laptop DVD drives are fairly standard, you just need to make sure whether it is SATA, or PATA (IDE) if a rather old laptop (10 years old?) because those 2 have different slot for connection. There are even adapters (caddy) which can allow you to install a second hard drive where a DVD drive was.

---

