---
title: "PXE-E53 error while installing UNR9.04"
date: 2009-09-18
forum: Installation &amp; Upgrades
---

### Post by Edaindil on 2009-09-18
Hi All,

Trying to switch from Ubuntu from Windows XP. I'm using a dell mini 10v and is trying to install UNR 9.04 i386.img via external USB drive.  The usb drive is a Western Digital 260 gig using FAT32.

So far, I've successfully written the .img onto the usb drive via flashnul. However, when I try to boot from the usb and install, it shows me info about my PCI ethernet card and then produces the following error:

PXE-E53: NO BOOT FILENAME RECEIVED
PXE-M0F: EXITING PXE ROM

I did some googling on the error and most of the results come back in regards to web server installs over PXE, but the instructions for installing UNR had no mention of PXE issues.

Can you tell me what I need to do to get past this error?

---

### Post by Partyboi2 on 2009-09-18
Hi, enter your bios and try changing your priority boot options so that you are booting from the usb external hard drive first, if you have not already done so.

---

### Post by Edaindil on 2009-09-18
I did that. When I have the usb drive plugged in, a plus sign appears in front of the usb option just like the HDD boot option. Whereas, CD/floopy/removable disk all have nothing. for example:
+ Harddrive
+ USB Drive
   Floopy
   DVD/CD
   Removable Drive

---

### Post by Edaindil on 2009-09-18
I'm thinking posting the error might help:

FOR REALTEK RTL 8101E/8102E(L)/8103E(L) PCI-E ETHERNET CONTROLLER V1.13 (081016)

CLIENT MAC ADDRESS: 01 25 E9 B5 7D A0 GUID: 45494C4C-4100-1040 8041-C3C01F354B31
PXE-E53: NO BOOT FILENAME RECEIVED
PXE-M0F: EXITING PXE ROM

INVALID PARTITION TABLE

---

### Post by Partyboi2 on 2009-09-19
Make sure + USB Drive is first in the list to boot from.
It also looks like you may have a invalid partition. A program you can use to fix partitions is [[COLOR=Blue]testdisk[/COLOR]]("http://members.iinet.net.au/%7Eherman546/p21.html")

---

### Post by Edaindil on 2009-09-19
I think I know the newb mistake I made now. After using flashnul, I didn't check my usb drive. But I now realized my 260 Gig drive only contains the boot files (totaling 1gig) and has 12 megs of free space. Ubuntu has no where to be installed. I thought  I was gonna be able to boot it via usb and install on harddrive. I'm about to partition the usb for about 2 gigs and leave rest of the drive for install.

---

### Post by Edaindil on 2009-09-19
After using flushnul, why does my 260 gig usb drive become a 1 gig drive? It only shows containing the UNR install files and 12 megs of free space...

---

### Post by Edaindil on 2009-09-19
At this point, I wrote the UNR.img using WinImage to my external. When trying to boot from the usb, it produces BOOT ERROR.

I can't use win32diskimager because when I click on the drop down menu for device, nothing shows up...

Thanks for the replies so far, btw.

---

### Post by Partyboi2 on 2009-09-19
If you have nothing you need to keep on your external hard drive, download [[COLOR=Blue]gparted[/COLOR]]("http://gparted.sourceforge.net/livecd.php") for usb and remove all partitions on the external hard drive and then create new partition(s).

---

### Post by Edaindil on 2009-09-19
I realized that win32diskimager only works with small flash drives for me. Once I plugged in a SD card in my reader, diskimager detected it and I wrote all the installation files on a SD card. Everything worked after that. Never got the other drive to work with an install. Thanks for all the input partyboi

---

