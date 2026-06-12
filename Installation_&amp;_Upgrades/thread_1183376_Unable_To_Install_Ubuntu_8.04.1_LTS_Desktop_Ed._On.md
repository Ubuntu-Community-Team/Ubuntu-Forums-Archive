---
title: "Unable To Install Ubuntu 8.04.1 LTS Desktop Ed. On My Computer. Need Your Help!"
date: 2009-06-10
forum: Installation &amp; Upgrades
---

### Post by montecarlo87 on 2009-06-10
[FONT=Calibri]Hello. First, I am new to Ubuntu. I am unable to install Ubuntu 8.04.1 LTS Desktop Edition from CD-ROM on my computer. I am a heavy Windows user and very familiar with installation processes with Windows XP & Vista. I have the Ubuntu 8.04.1 LTS Desktop Edition CD-ROM. I am installing this on a custom made computer. I have the ASUS P5Q (base model motherboard of the numerous P5Q speciality boards they offer) with 4GB RAM. The processor is the Intel Core 2 Quad CPU Q9550 2.83 GHz. I am installing this version of Ubuntu on a 80 GB hard drive Barracuda 7200.10 SATA. I am using the Nvidia GeForce 9600 GT graphics card. There are no partitions on this hard drive, since this drive is small in size, so the whole hard drive is a system drive. I am not sharing booting processes between Windows and Linux and not between the 2 Windows operating systems. All operating systems on my computer are on separate hard drives. I access all my operating systems through the BIOS at startup by selecting the primary bootup hard drive that has corresponding system installed on it.     [/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]What happens: I set the BIOS's primary boot drive to run from the DVD/CD-ROM drive and my secondary boot drive the 80 GB hard drive. After the system boots I get the Ubuntu screen that has the default option "Try Ubuntu without any change to your computer" and I change it to "Install Ubuntu" option. It shows the Ubuntu meter moving back and forth and then new black screen appears. It states, "BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash) Enter 'help' for a list of built-in commands." Following this information, "(initramfs)" and a flashing curser appears. That is where it stops. I have waited a few minutes and nothing happens. I do not know if this is correct or not in terms of the installation process of Ubuntu, but it would appear that it is not. [/FONT]
[FONT=Calibri]  [/FONT]
[FONT=Calibri] I get the same scenario using the default option "Try Ubuntu without any change to your computer." I even tried to install this version of Ubuntu on a Seagate IDE 80 GB Hard drive to see if the SATA HD has some bearing on the reason that is cannot install. It does not matter. I get the same scenario again. I wonder if my ASUS motherboard has some issues with installing Ubuntu? I wonder if my motherboard only is compatible with the Windows operating system? If anyone has any more suggestions, they would be appreciated. Thank you![/FONT]
[FONT=Calibri] [/FONT]
[FONT=Calibri]I need to know if Ubuntu can be installed on my hardware and system or not? If it can, what is the issue(s) that are causing the installation not to continue? What are the steps I need to take to properly install this version of Ubuntu on my system? Please keep your answers simplistic since I am new to this operating system. Thank you!   [/FONT]

---

### Post by jyaan on 2009-06-10
It _sounds_ like a hard disk problem to be, although I'm not 100% sure. When I had problems with an HD before I got that same kind of error. If you have a SATA HD, try setting it to AHCI mode, and if there is an option for "Change the DID for Linux" set that option, too.

---

### Post by pbpersson on 2009-06-10
> **jyaan said:**
> It _sounds_ like a hard disk problem to be, although I'm not 100% sure. When I had problems with an HD before I got that same kind of error. If you have a SATA HD, try setting it to AHCI mode, and if there is an option for "Change the DID for Linux" set that option, too.

I may be totally missing something here, but the OP said he tried a SATA drive and then a totally different drive that was IDE.  He got the same error both times.  How can you think it is a hard drive problem?  :o

Also, where are these AHCI and DID options found?  If these settings are somewhere in Ubuntu, please provide more detail as the OP said they know zero about Ubuntu.  I have been building machines and fooling with Ubuntu for years and I don't even know what you are talking about.

---

### Post by jyaan on 2009-06-10
Those are not Ubuntu settings, they're BIOS settings. Sorry for not being clearer on it.

---

