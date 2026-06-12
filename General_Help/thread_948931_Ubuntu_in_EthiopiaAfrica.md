---
title: "Ubuntu in Ethiopia/Africa"
date: 2008-10-15
forum: General Help
---

### Post by iksu on 2008-10-15
Hi, I work for an NGO that trains health professionals in Southern Ethiopia [(www.ethiopiagwentlink.org). ]("http://www.ethiopiagwentlink.org")My role is to promote e-learning.

Last year, I installed 6 PCs at health facilities in rural facilities. They are old P4 systems running Windows 2000 Professional. My past experience tells me that I should expect more than half of these should have major software issues when I go again this year. I was hoping to switch half of them over to Ubuntu (a case-control study?). No internet, e-learning material delivered in the form of videos, hmtl files and pdf files mostly with some proprietary windows software. There is no internet.

The following is the configuration of the computers.

     
**  Computer:  **
   Operating System   Microsoft Windows 2000 Professional  
   OS Service Pack   Service Pack 4  
   DirectX   4.09.00.0904 (DirectX 9.0c)  
   Computer Name   COMPUTER-1B8F48  
   User Name   Administrator  
   
 ** Motherboard:  **
   CPU Type   Intel Pentium 4, 1715 MHz (17 x 101)  
   Motherboard Name   Asus P4B533-VM (3 PCI, 1 AGP, 2 DIMM, Video)  
   Motherboard Chipset   Intel Brookdale-G i845G  
   System Memory   256 MB (PC2100 DDR SDRAM)  
   BIOS Type   Award Modular (06/09/02)  
   Communication Port   Communications Port (COM1)  
   Communication Port   Communications Port (COM2)  
   Communication Port   ECP Printer Port (LPT1)  
   [B]
  Display:  [/B]
   Video Adapter   NVIDIA GeForce2 MX 100/200 (32 MB)  
   3D Accelerator   nVIDIA GeForce2 MX 100/200  
   Monitor   Samsung SyncMaster 750(M)s(T) [17" CRT] (H8ONB00960)  
   
  **Multimedia:  **
   Audio Adapter   Intel 82801DB ICH4 - AC'97 Audio Controller [A-1]  
   
 ** Storage:  **
   IDE Controller   Intel(r) 82801DB Ultra ATA Storage Controller-24CB  
   Floppy Drive   Floppy disk drive  
   Disk Drive   IOMEGA ZIP 250  
   Disk Drive   WDC WD400BB-00DEA0 (37 GB, IDE)  
   Disk Drive   USB DISK 28X USB Device (972 MB, USB)  
   Optical Drive   LG CD-ROM CRD-8521B (52x CD-ROM)  
   Optical Drive   RDR-102 DVD-ROM  
   SMART Hard Disks Status   OK  
   
  **Partitions:  **
   C: (NTFS)   20010 MB (16855 MB free)  
   G: (NTFS)   18151 MB (7751 MB free)  
   Total Size   37.3 GB (24.0 GB free)  
  [B] 
  Input:  [/B]
   Keyboard   Standard 101/102-Key or Microsoft Natural PS/2 Keyboard  
   Mouse   HID-compliant mouse  
   [B]
  Network: [/B] 
   Network Adapter   Intel(R) PRO/100 VE Network Connection  
   
**  Peripherals: ** 
   USB1 Controller   Intel 82801DB ICH4 - USB Controller [A-1]  
   USB1 Controller   Intel 82801DB ICH4 - USB Controller [A-1]  
   USB1 Controller   Intel 82801DB ICH4 - USB Controller [A-1]  
   USB2 Controller   Intel 82801DB ICH4 - Enhanced USB2 Controller [A-1]  
   USB Device   USB Human Interface Device  
   USB Device   USB Mass Storage Device  


I have made a mirror of hardy repos on hard drive for some offline freedom. However, I would appreciate any advise the forum members can give me about what else I should be prepared for, given the system configuration above and the fact that I will be in the middle of nowhere and wont be going back for another year. I am not an expert but have been using Ubuntu for ~ 2years.

---

### Post by earthpigg on 2008-10-15
if you will be setting up an leaving, your solution needs to be fire and forget. 

the nice thing about live CD's is that they will let the locals fix whatever software they break. 

my suggestions:

- custom live cd of your chosen distro with all the software they will need
- make sure you teach a couple of the local**s** (no need to give one person all the power) how to use the live cd you will be leaving behind to re-install when/if they screw everything up. dont give them fish, teach them to fish :)
- partitioned hard drive... one for the OS, and one for /home (make sure you teach the locals why /home is on its own partition, and that they should be in the habbit of keeping anything they make/save there :)
- leave behind a 'distro x for dummies' book for your deputised tech support dudes to check out.
- bring a router and some CAT-5 so they can set up their own little LAN and play vidya games (or maybe even learn).

edit: DVD players may be expensive for these folks. make sure whatever you do, it includes the ability to play region-coded DVD's, etc.

---

### Post by ww711 on 2008-10-15
> **iksu said:**
> 
Last year, I installed 6 PCs at health facilities in rural facilities. They are old P4 systems running Windows 2000 Professional. My past experience tells me that I should expect more than half of these should have major software issues when I go again this year. I was hoping to switch half of them over to Ubuntu (a case-control study?)
The following is the configuration of the computers.

What's the reason for switching only potential half the number of your PCs? A uniform OS across all the systems would be easier to manage?

Things to consider? Timescales e.g fixing the current Windows systems? Installation of Ubuntu, re-training users, enough learning material e.g. books, pdfs, handouts, etc.

---

### Post by iksu on 2008-10-15
I am tempted to switch them all over as most of them have used computers very sparingly and therefore will be starting from scratch anyway. However (and this is a big HOWEVER), a lot of elearning material in medicine is available in proprietary formats for windows only. While some of these work with wine, most do not. I am trying to strike a balance between a computer that works year round with some vital medical information (UBUNTU) and another with the entire works but that could potentially crash and burn when the next cool guy decides to install the screensaver that he downloaded at the internet cafe on his weekly visit to the neighbouring city.

These folks do not have libraries or books and these computers are their only opportunity to keep their medical knowledge current. And, I can visit them only once or twice a year (from UK) and there is little local IT tech support. :(

I have been asked to install two computers at a local school in Yirgacheffee and here the decision was more straightforward - EDUBUNTU with all the bells and whistles.

And, there is the computer centre that they want at the regional medical school in Hwassa. 30 computers need to be networked and taken online (I am yet to find out what type of 'broadband' they have.) This is definitely beyond me (I am a surgeon by trade!!!) but will adivse on using Ubuntu and WiFi.

---

### Post by earthpigg on 2008-10-15
if networking 30 computers is beyond you, then bringing the router and some cat-5 cable on your six-computer-trip would really help you.... they dont expect you to network those three/six computers, so if you fail: no biggie. and if you can figure it out, you now know everything you need to network thirty of them.

---

### Post by iksu on 2008-10-20
Thanks for the advise. The computer library (yet to be setup) at Awassa is not really setup for a wired network - all the cables need to be run into walls etc.). Would it not be simpler to setup a wireless network? And, if so would Ubuntu present any quirks that will need to be taken care of?

---

### Post by jseiser on 2008-10-20
I dont know if ubuntu would run well with 256mb of ram.  You might want to look into DSL linux, puppy linux, slax or install kmandla gtk1.2 remix of ubuntu.

---

### Post by iksu on 2008-10-20
Well spotted,Jseiser! I realised that and got more sticks of 256. I am leaving on Friday for 2 weeks and will let you guys know how I got on. (Only part of the time is for computers; rest for some intesive trauma training!) When I come back, I am going to have a zillion questions about using Ubuntu for networking.

---

### Post by fballem on 2008-10-20
You might want to make sure that you take codecs with you on your distribution. Once you've converted a couple of the computers, including the codecs, you may want to test the library disks - they might be readable in ubuntu using the codecs.

Good luck. My parents have fond memories of Ethiopia - although they were there a very long time ago.

Regards,

---

### Post by shaggy999 on 2008-10-20
Another thing to remember is that if you're going to install non-free-codecs from medibuntu or ubuntu-restricted-extras you will run into problems because although you will have a copy of the packages, they are set to download things upon installation (such as the msttcorefonts and flash packages) directly from the internet.

---

### Post by iksu on 2008-11-05
From Addis airport - very successful trip. Learnt plenty of workarounds - will make a detailed post later.

---

### Post by earthpigg on 2008-11-06
looking forward to it :)

---

