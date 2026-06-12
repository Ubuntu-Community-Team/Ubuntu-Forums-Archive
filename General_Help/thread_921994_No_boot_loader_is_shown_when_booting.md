---
title: "No boot loader is shown when booting"
date: 2008-09-16
forum: General Help
---

### Post by cornel on 2008-09-16
Hello.

 I have a problem with my ubuntu installation. 
I dont get any Windows Bootloader after doing the Windows part of the installation and rebooting (write a password, select drive and size)

I have this working on another computer. Both of my computers is using Vista 64bit. 

Trying to install ubuntu 32bit on both.

---

### Post by cornel on 2008-09-17
Okay...
I might have upgraded the bootloader to Vista/Server 2008, using this Bootrec.exe and bootsect.exe

I got a currupted mbr from an ubuntu installation, and i fixed taht by one or more of this commands, it's a while ago, dont remember. 

Bootsect.exe /NT60 c:

Bootrec.exe /FixMbr
Bootrec.exe /FixBoot
Bootrec.exe /ScanOs
Bootrec.exe /RebuildBcd

I have tried to revert the changes by using bootsect.exe /nt52 but it didnt help me. 

How do i restore a bootsector that wubi can change? 

I have my Vista on C: and my Ubuntu on E: and nothing on D:

---

