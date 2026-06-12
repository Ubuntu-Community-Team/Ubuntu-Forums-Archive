---
title: "Big problem with NVIDIA binary driver in 8.04"
date: 2008-07-05
forum: Hardware
---

### Post by Desolator on 2008-07-05
Alright. I've had this problem on openSUSE 11 with KDE 4, but anyway:

After installing the NVIDIA binary driver via the "Hardware Drivers" tool, upon reboot and log-in, all I got was a nice orange background and the mouse cursor. After asking around in IRC, I cleaned the driver installed by that tool and installed the one from NVIDIA manually. Same problem. Same problem in openSUSE (and the reason ahy I went back to good 'ol Ubuntu).

The 'nv' driver works perfect, albeit without the 3D hardware acceleration, which is the main reason keeping me from wiping Windows and getting away from it (In a single word, Games :P). Now if you could try to help me, please, I'd be very greateful. If you also could present instructions for the "beginner" level if possible that's even better, cause I haven't touched any GNu/Linux distributino for a while, but I haven't forgotten the basics.

Right now I'm in Windows, and I can only use the terminal on Ubuntu, so that's sort of a problem. Plus the partitions are JFS (this has lways worked best for me), so I don't know of any tool to access those from Windows. I'm running Hardy Heron, x86_64, this are my computer specifications:

> Time of this report: 7/7/2008, 02:20:51
Machine name: CMIRCEA-WINDOWS
Operating System: Windows XP Professional (5.1, Build 2600) Service Pack 2 (2600.xpsp_sp2_gdr.070227-2254)
Language: English (Regional Setting: Romanian)
System Manufacturer: System manufacturer
System Model: System Product Name
BIOS: BIOS Date: 11/26/07 11:13:06 Ver: 08.00.12
Processor: Intel(R) Core(TM)2 Duo CPU     E8200  @ 2.66GHz (2 CPUs)
Memory: 2048MB RAM
Page File: 277MB used, 3662MB available
Windows Dir: C:\WINDOWS
DirectX Version: DirectX 9.0c (4.09.0000.0904)
DX Setup Parameters: Not found
DxDiag Version: 5.03.2600.2180 32bit Unicode

(Yea I was lazy and told DxDiag to tell me so I could just paste 'em here :P)

---

### Post by starcannon on 2008-07-05
Heres how I do all of my Nvidia installs,
[http://ubuntuforums.org/showpost.php?p=5086971&postcount=6](http://ubuntuforums.org/showpost.php?p=5086971&postcount=6)

The easiest way would be to set things back to running off the nv or vesa driver so that you can have a gui while doing the install, if this is not possible then you will need to make an adjustment to the guide since you do not have a gui to work with, each time you see:
```
gksudo gedit
```
replace that with
```
sudo nano
```
If you have no Ubuntu gui you will likely download the driver using windows, you will need to:
```
cd /location/of/driver
``` 
and follow the guide accordingly,as I assume you will either transport the driver using a usb stick, cd, or shared partition on the hard drive.

---

### Post by Desolator on 2008-07-05
That's the guide I used to simplify the proceeds of installing the NVIDIA driver ;)

> **starcannon said:**
> as I assume you will either transport the driver using a usb stick, cd, or shared partition on the hard drive.
Or copying it from the NTFS partition, or even installing directly from there :| Remember, NTFS-3G is available and installed by default.

---

### Post by Desolator on 2008-07-07
bumpy bumpa

---

