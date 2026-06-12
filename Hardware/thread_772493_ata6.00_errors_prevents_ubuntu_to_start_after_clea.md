---
title: "ata6.00 errors prevents ubuntu to start after clean installation"
date: 2008-04-28
forum: Hardware
---

### Post by jpkeisala on 2008-04-28
I have a strange error coming after I try to boot my machine. My PC boots into Ubuntu logo but hangs up to that for few minutes, then it jumps out from the Ubuntu boot logo to console view where it loops following error message and never goes out of loop:   
-----
```
ata6.00: status: {DRDY}
ata6.00: status: soft resetting link
ata6.00: status: configured for UDMA/33
ata6: EH Complete
ata6.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
ata6.00: cmd a0/00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in
			cdb 12 00 00 00 24 00 00 00    00 00 00 00 00 00 00 00 
			res 40/00:00:00:00:00:00:00:00:00:00:00 Emask 0x4 (timeout) 
```
-----

Is this hard disk error?  I have tried to reinstall Linux once but I keep getting same error. Any advice would be highly appreciate :confused:

Here is my hardware: 
Intel CORE2 QUAD Q6600 -BOX-2.4Ghz  1066 MHZ
ABIT S775 QUAD
Kingston- DDR2 PC800 8GB
HDD SATA-II 500Gb. Wester Digital
NVIDIA Gainw. FX 5500 AGP  DDR 256MB TV/DVI
Linksys PCi WIFI

---

### Post by kaiataris on 2008-04-28
I'm having the same problem, but not from a clean install.

I installed Ubuntu via Wubi 8.04, and the base install went fine
once I tried to install linux-rt kernel (I wanted to upgrade to Ubuntu Studio)then I get the problem with the hanging and freezing
with Buffer I/O errors and ata6 errors.

I had Wubi install Ubuntu to NTFS formated partition. I'm thinking that's the problem (the generic kernel seems fine)but I'm not sure. Are you on regular Ubuntu or UbuntuStudio with a Realtime kernel?

-Kai

---

### Post by jpkeisala on 2008-04-29
> **kaiataris said:**
>  Are you on regular Ubuntu or UbuntuStudio with a Realtime kernel?

This is regular 64bit Ubuntu, burned from ISO file, formatted disk with no other OS's running. Live CD works fine but I have tried 2 times to install this and it fails both times same way.

---

### Post by TheConqueror on 2008-06-06
Hi,

I'm getting this same error when trying to run from the live CD or install.  At the console I'm looking in the casper.log file (not asure what that is), but it says "cannot open /dev/sdc" and "cannot open /dev/sdc1" and "unable to find medium containing a live file system".

This machine has one ATA drive and 2 SATA.  The ATA has MCE installed at the moment.  I just wanted to try mythbuntu as a replacement.

Has anyone got any suggestions of how to trouble-shoot this problem.  I'm not that familiar with ubuntu.

Thanks,

Allen

---

### Post by jpkeisala on 2008-06-07
> **TheConqueror said:**
> Hi,
Has anyone got any suggestions of how to trouble-shoot this problem.  I'm not that familiar with ubuntu.



Unforunally I never got any help on this seems like very unique error. I had to give up with Ubuntu on this machine.

---

### Post by TheConqueror on 2008-06-07
> **jpkeisala said:**
> Unforunally I never got any help on this seems like very unique error. I had to give up with Ubuntu on this machine.

What did you use instead ?

---

### Post by jpkeisala on 2008-06-08
> **TheConqueror said:**
> What did you use instead ?

This ATA error is specific for this release of Ubuntu. I was planning to downgrade back to older version of Ubuntu which runs just fine but in the end I installed Windows 2008 server, you can download trial which lasts 180 days. I am running it until next version of ubuntu. Though, Win2008 server is really good but you need to do some tweaking to get it run smoothly as workstation.

---

### Post by TheConqueror on 2008-06-08
> **jpkeisala said:**
> This ATA error is specific for this release of Ubuntu. I was planning to downgrade back to older version of Ubuntu which runs just fine but in the end I installed Windows 2008 server, you can download trial which lasts 180 days. I am running it until next version of ubuntu. Though, Win2008 server is really good but you need to do some tweaking to get it run smoothly as workstation.

I'm actually trying to get mythTV working on my HTPC and get this error.  I'll try using an older version og mythbuntu based on Gutsy (trying Hardy at the moment).

---

