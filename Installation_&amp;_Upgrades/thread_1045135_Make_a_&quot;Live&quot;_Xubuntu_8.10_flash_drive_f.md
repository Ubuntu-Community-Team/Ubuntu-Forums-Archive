---
title: "Make a &quot;Live&quot; Xubuntu 8.10 flash drive from an Xp Machine"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by byngo on 2009-01-20
Hi,
I have a modern Acer notebook that has a defective IDE controller & therefore the HDD and CD/DVD Rom work intermittently.
I managed to get Ubuntu 8.10 installed using the CD ROM and a live CD and installed a persistent USB flash drive jobby which works quite well.

I wanted to try Xubuntu 8.10 on the laptop using an alternative flash drive but my CD Rom drive reliability is getting worse.

My question is, how can I create a Live (persistent) Xubuntu install to a USB flash drive using my other machine which runs XP pro.
I found the pendrivelinux website and think there is the answer but I must be sure that the XP machine will not be affected at all. A summary of the instructions there are as follows:

_[I]Essentials for creating a Xubuntu 8.10 Live USB:_ 

[I]Windows PC to perform conversion 
Xubuntu 8.10 ISO (the script can download it)

2GB or larger USB flash drive

Xubuntu810p.exe (contains the files to do the conversion) 
HP USB format tool (to format and make the flash drive active) 
How to Create a Live USB Kubuntu 8.10 Flash Drive:

Download the HP USB format tool and format your stick using a Fat32 file system 
Download and launch Xubuntu810P.exe, extracting to your Computer, a Xubuntu810P folder is created 
Download the Xubuntu 8.10 ISO and place it in the Xubuntu810P folder on your PC. This step is optional, the script will attempt to download the ISO if it is not present 
From the Xubuntu810P folder, click Xubuntu810.bat and follow the onscreen instructions 
Once the script has finished, restart your PC and set your BIOS or Boot Menu to boot from the USB device, save your changes and reboot 
You should now have your own personal Live USB Xubuntu 8.10 that will save any changes that you make and restore them on subsequent boots.[/I][/I]

Are these the instructions I need so that the XP machine will not be disturbed and the pen drive will boot xubuntu on my laptop?

Thanks in advance.
Byngo.

---

### Post by C.S.Cameron on 2009-01-20
Unetbootin for Windows using the Xubuntu 8.10 iso is probably the simplest method to make what you want.
There are several methods to make an Unetbootin install persistent.

---

### Post by byngo on 2009-01-20
> **C.S.Cameron said:**
> Unetbootin for Windows using the Xubuntu 8.10 iso is probably the simplest method to make what you want.

Thanks for the reply.
I did'nt think the instructions i quoted from pendrive linux were difficult, in fact quite straight forward. Its just that i wanted to be sure not to disturb my XP installation on the other machine.
I also wanted the Live USB to be persistent.
I will look into Unetbootin though & see if it looks right for me.

---

### Post by byngo on 2009-01-21
> **C.S.Cameron said:**
> Unetbootin for Windows using the Xubuntu 8.10 iso is probably the simplest method to make what you want.
There are several methods to make an Unetbootin install persistent.

Ok, I tried the pendrivelinux method i listed an it failed to boot.
Looked into unetbootin and looks good.
You said there are several methods of making a bootable USB pendrive installation be persistent.

Please can you advise what addition steps i need to take above those provided by default in the Unetbootin process or after the Unetbootin creation to make it persistent please. Im a complete newbie to Linux but moderately experianced with XP.

---

### Post by C.S.Cameron on 2009-01-23
See
[http://ubuntuforums.org/showthread.php?t=811397](http://ubuntuforums.org/showthread.php?t=811397)
Post 4
This method may work with 8.10.
Post 38
Is what worked for me.

---

