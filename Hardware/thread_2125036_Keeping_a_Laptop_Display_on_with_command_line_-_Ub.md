---
title: "Keeping a Laptop Display on with command line - Ubuntu Server (no GUI)"
date: 2013-03-12
forum: Hardware
---

### Post by the ginger on 2013-03-12
I've been searching far and wide, to no avail. 
I want Ubuntu Server to "do nothing" when I close the lid of my laptop.

I'm running Ubuntu Server 12.10, with no GUI.

Any help is greatly appreciated!

---

### Post by tgalati4 on 2013-03-12
This is a tough one, because most lid action is controlled by BIOS, which you may or may not have control over.  There is *acpitool* which allows you to turn things on and off.

tgalati4@Mint14-Extensa /proc/acpi $ cat wakeup
Device	S-state	  Status   Sysfs node
LID0	  S3	*enabled   
SLPB	  S3	*enabled   
HDEF	  S3	*disabled  pci:0000:00:1b.0
PXSX	  S5	*enabled   pci:0000:02:00.0
USB1	  S3	*enabled   pci:0000:00:1d.0
USB2	  S3	*enabled   pci:0000:00:1d.1
USB3	  S3	*enabled   pci:0000:00:1d.2
EHC1	  S3	*enabled   pci:0000:00:1d.7

For instance, using *acpitool* to disable LID0 may give you the behavior that you want.

tgalati4@Mint14-Extensa ~ $ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID0	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. HDEF	  S3	*disabled  pci:0000:00:1b.0
  4. PXSX	  S5	*enabled   pci:0000:02:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB2	  S3	*enabled   pci:0000:00:1d.1
  7. USB3	  S3	*enabled   pci:0000:00:1d.2
  8. EHC1	  S3	*enabled   pci:0000:00:1d.7

In my case:

```
sudo acpitool -W 1
```  should disable the LID0.  Your device number may be different.

---

### Post by the ginger on 2013-03-13
I downloaded *acpitool*, ran it, and got the following:

eris@eris:~/Desktop$ acpitool -w
   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. HDEF	  S3	*disabled  pci:0000:00:1b.0
  2. PXS1	  S4	*disabled  
  3. PXS2	  S4	*enabled   pci:0000:03:00.0
  4. PXS3	  S4	*disabled  pci:0000:04:00.0
  5. USB1	  S3	*enabled   pci:0000:00:1d.0
  6. USB5	  S3	*enabled   pci:0000:00:1a.1
  7. EHC1	  S3	*enabled   pci:0000:00:1d.7
  8. EHC2	  S3	*enabled   pci:0000:00:1a.7

I don't see anything resembling a LID0 like yours. Any suggestions?

---

### Post by the ginger on 2013-03-13
I don't know if it helps at all, but a few weeks ago when I initially set up this server, I ran across the same problem. I googled the problem, found a solution, and fixed it with a few short lines of code. Unfortunately, since then I have forgotten the code, and switched from Opera to Chrome, and lost my web history. I also spent a good 3 hours searching on google today to no avail.

All in all, I know it can be fixed with code, I just can't remember how.

---

### Post by mellocode on 2013-03-13
Does this question on askubuntu solve your problem? [http://askubuntu.com/questions/141866/keep-ubuntu-server-running-on-a-laptop-with-the-lid-closed](http://askubuntu.com/questions/141866/keep-ubuntu-server-running-on-a-laptop-with-the-lid-closed)

---

### Post by the ginger on 2013-03-13
Ahh! Thank you so very much mellocode, that seems so have worked.

---

