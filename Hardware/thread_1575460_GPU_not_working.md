---
title: "GPU not working??"
date: 2010-09-15
forum: Hardware
---

### Post by esweinstein on 2010-09-15
I have recently built my first system. here are the main specs:

GA 880GMA UD2H - Motherboard

AMD Phenom II X4 955 - CPU

G-Skill 4GB (2X2GB) 1600 (running at 1333)- RAM

Asus MS236 23" Widescreen - Display

and lastly:

HIS ATI Radeon HD 5670 1GB - Graphics Card

I put the hardware together and i was having trouble loading the operating system(Ubuntu 10.04 - 64 bit). I tried a couple of different things. I finally realized that the problem was with the graphics card. I think Ubuntu was having trouble working with the card without a driver. anyway, loaded the operating system without the card (the motherboard has an onboard chip - Radeon HD 4250). everything went smooth. Now i wanted to install the higher end graphics card and it just won't work!!! I activated the proprietary driver (FGLRX) and it still won't work. I consulted the Terminal checked "fglrxinfo" and it sent back "Segmentation Fault"... i don't know what to do. Looking for help...

---

### Post by breem42 on 2010-11-16
Hi.  I can't solve your problem, but maybe you can solve mine.

I recently bought a system with a Gigabyte GA-880GMA-UD2H (Rev 2.1) MB.  I'm using the onboard Radeon HD 4250.  I downloaded & burned 10.04 (64 bit version), and tried to get it to boot from it.  So far it won't.

First I checked to see that the BIOS settings were correct -- that it would try to boot from the optical drive.  Yup -- CDROM was first.  Then I changed all boot drives to CDROM.  Still boots to Win7 :confused:.

I've updated the BIOS to version 5.

BTW it won't boot from a GParted CD, or any other disk that my old machine booted from perfectly.  I need to use GParted to make an ext partition.

How did you get it to boot from a CD?

Thanks in advance.

---

### Post by mastablasta on 2010-11-16
> **breem42 said:**
>  
First I checked to see that the BIOS settings were correct -- that it would try to boot from the optical drive. Yup -- CDROM was first. Then I changed all boot drives to CDROM. Still boots to Win7 :confused:.
 
 
 
that is just boot order, so what happens i sthat it checkes the CD first. if everyhting is ok with the CD and the system on it it will boot form cd, otherwise it will skip it and go to hard disk to search for the system.
 
therefore something is either wrong with your CD (bad download, corrupet CD, bad burn?!) or CD drive.
 
you could try with a USB key if you have one... also they are cheap to buy.

---

### Post by breem42 on 2010-11-16
OK, so I figured it out.

My DVD drive was not marked as CDROM as I expected, instead listed a code name (like DVD-BLARG -- can't remember what it was at the moment) at the very end of the list.

Easy fix to bios settings.  Now I'm configuring my new Lucid install.

BTW did you ever solve your GPU problem?

---

