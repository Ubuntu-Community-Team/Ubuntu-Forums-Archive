---
title: "My Pc is slow...why?"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by Mcjensen on 2006-01-05
The install went very fine.:)..after some tinkering , I got my mouse working in USB, I got my sound working, and Im getting more comfortable using Linux for the first time. [COLOR="Red"]All in all [/COLOR]things are working well.
     One problem though is my PC is slow....I have a compact Presario 7450, km6-2 475 mhz, 512 Ram....is there anyway I can make Ubuntu run faster or does it just need a better motor?  Im running windows 2000 on the first hard drive and that runs fine.  Also, are there any defragmenters or error scanners on Ubuntu? Overall Im very impressed with the desktop and the ease in which the installation went, Quite impressive for a free operating system, Mcjensen:cool:

---

### Post by Mcjensen on 2006-01-05
Answers?

---

### Post by etc on 2006-01-05
Try out xfce instead of Gnome
```
sudo apt-get install xubuntu-desktop
```
in a terminal 

Or open up System -> Administration -> Synaptic Package Manager, click search, search for xubuntu-desktop, right click -> Mark for installation, then click Apply.
Logout, click Session, then choose Xfce Desktop.

Also 475 mhz is pretty slow.

You also don't have to defragment ext3, which is what Ubuntu uses

---

### Post by welsh_spud on 2006-01-05
You may like to try a different desktop environment. Search in Synaptic for xubuntu-desktop and install it. Its a more lightweight desktop.

Does your computer have _any_ video ram. If you can get that working then you may be able to accelerated desktop. Which means that you wouldn't get those butt ugly lines when you move a window.

....and you shouldn't worry about linux fragmenting. Ubuntu linux uses a different file system to windows. Ubuntu uses ext3, where Windows uses NTFS (and in older versions used FAT32)


EDIT - Damn, I should have clicked submit before I got that sandwich! :(

---

### Post by Mcjensen on 2006-01-05
Alright...I uploaded the other desktop and it runs better smoother than Gnome did on this old Jalopy... 
Ill have to try Ubuntu on my newer PC for a fair evaluation....thanks for your help, McJensen :cool:

---

### Post by garnertr on 2006-01-05
[QUOTE=Mcjensen]Alright...I uploaded the other desktop and it runs better smoother than Gnome did on this old Jalopy... 
Ill have to try Ubuntu on my newer PC for a fair evaluation....thanks for your help, McJensen :cool:[/QUOTE]


Which one did you use?

---

### Post by Mcjensen on 2006-01-06
I loaded up xfce instead of Gnome, but I may try Kde soon, Thanks McJensen :cool:

---

### Post by Perfect Storm on 2006-01-06
If you install 3D card driver it will also boost performance if you have a 3d card.

---

### Post by tabinin on 2006-01-06
[QUOTE=Mcjensen]One problem though is my PC is slow....I have a compact Presario 7450, km6-2 475 mhz, 512 Ram....[/QUOTE]

Your other issue may be a slow hard drive.  I have seen a few older Comaqs with 4,000 RPM drives (booo!), which are real dogs.  If you have a newer (7200 RPM) drive, check to make sure dma is enabled:

```
sudo hdparm -v /dev/hda
```

---

### Post by Mcjensen on 2006-01-06
[COLOR="Red"][INDENT]Artificial Intelligence 
> If you install 3D card driver it will also boost performance if you have a 3d card. [/INDENT][/COLOR]

I have a 3d care working on my first had drive with windows 2000, but how do I install a linux 3d card driver for my second hard drive with Ubuntu? Mcjensen:cool:

---

### Post by Gray. on 2006-01-06
Do you have Nvidia or ATI card?

---

### Post by Mcjensen on 2006-01-06
Heres some of my PC specs;

**_Motherboard_**	
CPU Type	AMD K6-2, 475 MHz (5 x 95)
Motherboard Name	Compaq Compaq PC
Motherboard Chipset	VIA VT8501 Apollo MVP4
System Memory	503 MB  (SDRAM)
BIOS Type	Compaq (07/25/00)

**_Display	_**
Video Adapter	VIA Tech VT8501 Graphics Controller  (8 MB)
3D Accelerator	Trident Blade3D i7
Monitor	HP D8905  (CN10638860)
	
Multimedia	
Audio Adapter	ESS Technology Allegro-1.COMM AudioDrive
	
Storage	
Disk Drive	ST38410A  (8 GB, 5400 RPM, Ultra-ATA/66)

Partitions	
G: Ubuntu (EXT2)	7632 MB (5618 MB free)
H: Swapdrive          500Mb
M: (FAT32)	4988 MB (4445 MB free)
	
Input	
Keyboard	Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse	HID-compliant mouse
Mouse	PS/2 Compatible Mouse
	
**_Chipset Properties	_**
Motherboard Chipset	VIA VT8501 Apollo MVP4
External Cache Size	512 KB
External Cache Type	Synchronous Pipelined Burst
External Cache Status	Enabled
	
**_Integrated Graphics Controller	_**
Graphics Controller Type	Trident CyberBlade
Graphics Controller Status	Enabled
Graphics Frame Buffer Size	8 MB
	
Memory Slots	
DRAM Slot #1	256 MB (SDRAM)
DRAM Slot #2	256 MB (SDRAM)
	
AGP Properties	
AGP Version	2.00
AGP Status	Enabled
AGP Aperture Size	64 MB
Supported AGP Speeds	1x, 2x
Current AGP Speed	2x
Fast-Write	Not Supported
Side Band Addressing	Supported, Enabled

---

### Post by Mcjensen on 2006-01-06
Hi , 
I guess whats really slow is my internet...Im using a usb surfboard modem...works fine with windows 2000, but maybe its got a problem here, McJensen :confused:

---

### Post by newuser111 on 2006-01-08
you could try fluxbox, its the best of all of light window managers imho, since it comes with a dockbar unlike openbox

the only hard thing is setting up the menus, which isnt that difficult if you do some reading, also you may want to pick a file manager, i recommend gentoo or krusader from synaptic

---

