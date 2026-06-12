---
title: "No sound, No WLAN, No NTFS HD, HELP!"
date: 2005-05-21
forum: Hardware &amp; Laptops
---

### Post by dtsdude on 2005-05-21
Hi,
Just finished assembeling my new box, i cant connect to the wireless network and theres no sound. Also i cant access my 80 and 120 gig HD's which are packed full with media.  The sound and access to the HD's was no problem when i tried Xandros, but even there i couldent get the wlan to work.

Heres my hardware:
MOBO: Gigabyte GA-K8NF-9 nForce4-4X chipset
WLAN: Netgear 54 Mbps PCI WG311
CPU: AMD Athlon 64 3000+
RAM: 512MB
Graphic: nvidia GeForce 6200 128MB PCI-X
HD1: 3.2 gig Fujitsu (if im not mistaken)
HD2: 120 gig Samsung
HD3: 80 gig S-ATA Samsung

OS: Ubuntu 64bit edition.

P.S. Im a total new-b to linux (e.x. windows addict) so i need detailed info.

Thanx in advance.

Patrick

---

### Post by FreeEagle on 2005-05-21
about the NTFS Hard disk you have to do this : 


First Read this and follow the instructions :

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

this will help you to automount your HDs.


now about you Wirless Card you have to download and install this Driver form this site and hope it will work .
[http://acx100.sourceforge.net/](http://acx100.sourceforge.net/)

Good luck 


FreeEagle

---

### Post by dtsdude on 2005-05-22
woo, fast reply...   :smile:
But i dont know how to install the driver and how do i download it, been using M$ since win95, so im kinda lost when the download dosent install automaticly.
Also i followed the instructions to detect the ntfs partitions, but when i look in /mnt all i find is a empty folder named "windows".
Part from that, i managed to fix my sound problem, ](*,)  the speakers were unpluged.



EDIT:
I have no idea what "CVS" and "Tarballs" is. I even tried terminal "user@c83-249-8-118:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 login
bash: cvs: command not found"
That didint help.

 [http://acx100.sourceforge.net/download.htm](http://acx100.sourceforge.net/download.htm) l.............
 "Download

Note: since CVS and SF content is not maintained at the moment, please refer to Tarballs below.
CVS
To obtain a copy of the driver via CVS, please do the following:
$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 login
$ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 co acx100
When prompted for a password, just hit Enter.

The CVS versions have also been tagged as acx100_0_1c, acx100_0_1d and acx100_0_1e, and so on.

Due to the current extreme lag of the public SourceForge CVS server, it may take about a day for the changes to arrive in public CVS. The driver version can be verified e.g. using "cvs log README".
Note that the CVS server is also pretty"

---

### Post by FreeEagle on 2005-05-22
[QUOTE=dtsdude]woo, fast reply...   :smile:
But i dont know how to install the driver and how do i download it, been using M$ since win95, so im kinda lost when the download dosent install automaticly.
Also i followed the instructions to detect the ntfs partitions, but when i look in /mnt all i find is a empty folder named "windows".
Part from that, i managed to fix my sound problem, ](*,)  the speakers were unpluged.



EDIT:
I have no idea what "CVS" and "Tarballs" is. I even tried terminal "user@c83-249-8-118:~$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 login
bash: cvs: command not found"
That didint help.

 [http://acx100.sourceforge.net/download.htm](http://acx100.sourceforge.net/download.htm) l.............
 "Download

Note: since CVS and SF content is not maintained at the moment, please refer to Tarballs below.
CVS
To obtain a copy of the driver via CVS, please do the following:
$ cvs -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 login
$ cvs -z3 -d:pserver:anonymous@cvs.sourceforge.net:/cvsroot/acx100 co acx100
When prompted for a password, just hit Enter.

The CVS versions have also been tagged as acx100_0_1c, acx100_0_1d and acx100_0_1e, and so on.

Due to the current extreme lag of the public SourceForge CVS server, it may take about a day for the changes to arrive in public CVS. The driver version can be verified e.g. using "cvs log README".
Note that the CVS server is also pretty"[/QUOTE]


do not look in mnt , you have to look in Media and you will find your WIndows Partion there, about the driver you can download the Tarballs instead of doing that CVS .... go to download from here : [http://rhlx01.fht-esslingen.de/~andi/acx100/](http://rhlx01.fht-esslingen.de/~andi/acx100/)


Best Regards,
 FreeEagle

---

### Post by dtsdude on 2005-05-22
was a bit complicated, but i managed to get it working.
they should include this in future releases of ubuntu :smile: 
or at least make a .deb file with all the drivers, 

thanx alot

peace

---

### Post by FreeEagle on 2005-05-22
you welcome, i am happy that you could do it yourself with these tips...


Enjoy Linux!!!!


FreeEagle

---

