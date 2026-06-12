---
title: "Help!!!!!!! Display problems!"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by King Edward on 2009-11-01
Hello,

I just installed ubuntu 9.10 with Wubi but I am having problems with the resolution. It is stuck in 800x600 and in WIndows 7 it is capable of 1280x800. Please can anyone tell me how to 'force' Ubuntu to run in 1280x800. I am brand new to Linux so please don't use jargon as I won't be able to understand it!!!

Thank you very much!

(I've attached a screenshot of my desktop)

[ATTACH]134090[/ATTACH]

---

### Post by macogw on 2009-11-01
Can you open a Terminal (Applications -> Accessories -> Terminal) and type in ```
lspci
``` so we can see what kind of graphics card you have?

---

### Post by floweringmind on 2009-11-01
Do you have an ATI card? Because on my laptop there were no restricted drivers for it. So I went to ATI downloaded the video driver from there and it installed beautifully.

Chris

---

### Post by davidw19125 on 2009-11-01
:popcorn:Hi I upgraded from Ubuntu 9.4 to the new Ubuntu 9.10 ever thing went ok on he install but the screen size went from 1280 x 1024 that I had in Ubuntu 9.4 to 800 x 600 in the Ubuntu 9.10. Went I try to set it back to the 1280 x 1024 it change it but then it would not shout down any more and I would have to reboot it in to windows and then shout down thw computer. So I didn't like the way it was working and after trying to fix it I reinstalled the old Ubuntu 9.4 Ubuntu 9.4. Then I could not get that to the screen size I wanted it told me I had to install a new driver so I did and that didn't help at all. I see on here that there are some other people having trouble with the same thing I surm would like to find a fix for this problem I'm having so I can run the Ubuntu software.
                                                                                                              Thanks

                                                                                                                        Davidw19125

---

### Post by King Edward on 2009-11-01
> **macogw said:**
> Can you open a Terminal (Applications -> Accessories -> Terminal) and type in ```
lspci
``` so we can see what kind of graphics card you have?


Here is the information displayed:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Basically it's a SIS Mirage 3 graphics card.

---

### Post by davidw19125 on 2009-11-01
> **davidw19125 said:**
> :popcorn:Hi I upgraded from Ubuntu 9.4 to the new Ubuntu 9.10 ever thing went ok on he install but the screen size went from 1280 x 1024 that I had in Ubuntu 9.4 to 800 x 600 in the Ubuntu 9.10. Went I try to set it back to the 1280 x 1024 it change it but then it would not shout down any more and I would have to reboot it in to windows and then shout down thw computer. So I didn't like the way it was working and after trying to fix it I reinstalled the old Ubuntu 9.4 Ubuntu 9.4. Then I could not get that to the screen size I wanted it told me I had to install a new driver so I did and that didn't help at all. I see on here that there are some other people having trouble with the same thing I surm would like to find a fix for this problem I'm having so I can run the Ubuntu software.
                                                                                                              Thanks

                                                                                                                        Davidw19125


Hi I installed Ubuntu 9.04 again to day I was having trouble with it after I did the upgrade to Ubuntu 9.19 and after I deleted it and them istalled the Ubuntu 9.04 again I was having trouble with the screen size only being 800 x 600 and when I tryed to fix it buy installing the voedo driver it said I needed it started to get me a problem that the computer montor would go to sleep and the only way to get it to run or come back on again was to reboot the system. After I installed it this time I first check the screen saver and it was turn on and I didn't have it turn on be fore so I turn that off and that fixed that problem. As far as the screen size I reinstalled the viedo driver that I needed and it worked and I can set the screen size to any thing I want now. 
 Now all this trouble started after I installed the new update Ubuntu 9.10 s I think they have some thing not right and they will have to work on it. The only other thing that could be going on is when you download it from the Ubuntu web page you get the BATA of it and not the final version of the software. Because they tell you on there web site to go to the BITTORRENT to download the program. 
 Sorry this is so long just though it might help someone out or give them so Idea what to look for.
            Davidw19125
:popcorn:

---

### Post by JBAlaska on 2009-11-01
> **King Edward said:**
> Here is the information displayed:

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 671MX
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS968 [MuTIOL Media IO] (rev 01)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] 191 Gigabit Ethernet Adapter (rev 02)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] SATA Controller / IDE mode (rev 03)
00:0f.0 Audio device: Silicon Integrated Systems [SiS] Azalia Audio Controller
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 771/671 PCIE VGA Display Adapter (rev 10)

Basically it's a SIS Mirage 3 graphics card.
I found a Thread for your video chip-set [Here](http://ubuntuforums.org/showthread.php?t=615094&highlight=M671) and read through all 206 posts for you, sadly there is no 3d driver available at this time, however the 2D driver should allow you to set your proper resolution.
A Ubuntu user in that thread maintains a wiki site [Here](http://ncc-1701a.homelinux.net/~linux-sis/) with the latest available drivers and config info (Sadly still 2D only).

Good Luck!

---

### Post by King Edward on 2009-11-02
> **JBAlaska said:**
> I found a Thread for your video chip-set [Here](http://ubuntuforums.org/showthread.php?t=615094&highlight=M671) and read through all 206 posts for you, sadly there is no 3d driver available at this time, however the 2D driver should allow you to set your proper resolution.
A Ubuntu user in that thread maintains a wiki site [Here](http://ncc-1701a.homelinux.net/~linux-sis/) with the latest available drivers and config info (Sadly still 2D only).

Good Luck!

Excellent!! Thank you very much!

---

