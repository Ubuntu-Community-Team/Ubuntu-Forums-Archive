---
title: "Simple Ubuntu 9.04 and Windows 7 dual boot solution"
date: 2009-08-07
forum: Installation &amp; Upgrades
---

### Post by T-n-T Handywork on 2009-08-07
I'm relatively new to the Ubuntu community and have read several posts regarding the dual boot installation process for Ubuntu and Windows 7. I plan to build a test system with a single HDD and maybe later try two HDDs when my skill level is higher. Could someone please provide simple instructions (as I'm simple minded) on how to setup this dual boot. I don't wish to run Win 7 in a virtual environment as my intent is to end up with a system with two drives where one is dedicated to Win 7 and one to Ubuntu. BTW is it just me or does Win 7 seem to have "borrowed" a lot from Ubuntu and OS x? Thank you in advance for your help.

---

### Post by merlinus on 2009-08-07
Although this is for vista, I imagine it would be about the same:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

---

### Post by T-n-T Handywork on 2009-08-07
Thanks, I'm going to try this weekend.

---

### Post by gordintoronto on 2009-08-07
> **T-n-T Handywork said:**
> Thanks, I'm going to try this weekend.

I just installed Windows 7 and Ubuntu last week on a blank hard drive, which is actually easier.  I installed Windows 7 first, telling it to use 60 GB of the available 600 GB.  Then I installed Ubuntu by booting from the CD, telling its partition editor to use 40 GB for the root ( / ) partition, 8 GB for the swap (twice my memory size) and the remainder for the Home partition.  Grub lets me choose what I want to run; Ubuntu is my "production" system, Windows 7 is only there as a learning tool.

It's working beautifully.  Ubuntu has complete access to the Windows partition, but I don't have the EXT3 driver loaded in Windows, so Windows is limited to 60 GB.

---

### Post by Mark Phelps on 2009-08-08
> **T-n-T Handywork said:**
> BTW is it just me or does Win 7 seem to have "borrowed" a lot from Ubuntu and OS x?

There are only so many ways to do things with any desktop PC, so it's not unusual to see similar functions and GUIs in each. Some say it's borrowing; others say it's stealing.

But, I say "so what"? Given the price of Windows 7, the more they put into it (regardless of where they got that), the more you get for your money.

---

### Post by T-n-T Handywork on 2009-08-08
I don't disagree with you. If your going to have to pay for an operating system, it should be loaded with useful applications. That is one of the reasons that I'm impressed with Ubuntu. It has useful applications and is not bloated with "trial software" and such. Although my commentary regarding the likeness of Windows 7 to Ubuntu was meant to be in jest;  the likeness is not necessarily a bad thing as the GUIs similarity makes navigation for newcomers easier when switching between operating systems.

---

### Post by T-n-T Handywork on 2009-08-08
> **gordintoronto said:**
> I just installed Windows 7 and Ubuntu last week on a blank hard drive, which is actually easier.  I installed Windows 7 first, telling it to use 60 GB of the available 600 GB.  Then I installed Ubuntu by booting from the CD, telling its partition editor to use 40 GB for the root ( / ) partition, 8 GB for the swap (twice my memory size) and the remainder for the Home partition.  Grub lets me choose what I want to run; Ubuntu is my "production" system, Windows 7 is only there as a learning tool.

It's working beautifully.  Ubuntu has complete access to the Windows partition, but I don't have the EXT3 driver loaded in Windows, so Windows is limited to 60 GB.


I did basically the same thing, although the hard drive had XP Pro and Ubuntu 9.04, I installed Win 7 and left the Ubuntu partitions alone. Of course Grub was trashed, but I was expecting that and planned a fresh install of Ubuntu anyway. I installed on a Panasonic Toughbook with a 1.6 Ghz CPU and 512mb of ram. Surprisingly, Win 7 is functional even though my laptop is below par on specs for Win 7. As always Ubuntu loaded fine and I have an opportunity to test both operating systems.

---

### Post by Carlos007 on 2009-08-08
I used WUBI it sorts most of the partitioning out for you.. well now i just use two seperate h/d  if i want to boot my xp i just simply swap them.. a long process i know.

Also i am wondering if a usb portable version of xp will work?



Wubi can be downloaded here  [http://wubi-installer.org/latest.php](http://wubi-installer.org/latest.php)

---

### Post by presence1960 on 2009-08-08
Wubi is not intended to be used as a permanent solution, but rather as a test drive for those who don't want to partition their hard disk for now.
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)
Also note further down the page that wubi may be subject to performance degradation due to windows filesystem fragmentation. The community documentation says that wubi allows a windows user to **_try Ubuntu_** - try being the key word. Once you use wubi and decide you like Ubuntu it is better to partition your hard disk and do a full install. The trial would thus be over.

---

### Post by presence1960 on 2009-08-08
> **Carlos007 said:**
> I used WUBI it sorts most of the partitioning out for you.. well now i just use two seperate h/d  if i want to boot my xp i just simply swap them.. a long process i know.


Why don't you install GRUB to MBR of your Ubuntu drive and set that drive to boot first in the hard disk boot order in BIOS. You would then have GRUB come up on boot and you will be able to boot Ubuntu and windows from GRUB. An added benefit of doing it this way is since your windows and ubuntu are on different hard disks your windows bootloader on MBR of your windows disk will remain intact if you install GRUB to MBR of the ubuntu disk. No need to be switching hard disks, plugging or unplugging.

---

### Post by T-n-T Handywork on 2009-08-09
Good comments on GRUB. Now a GRUB question. I dual booted with Ubuntu 9.04 and Windows 7 and a single hard disk laptop that I spoke of earlier in this thread. Today, I turned it on and it gave me error 18. Any thoughts? I did read about the error, but thought it would have surfaced last night as I did turn it off for awhile and then back on with no problem. I do have concerns about the health of my hard disk as it seems not to be running as good as it used to. I also noticed before I installed windows 7 that GRUB took forever to appear and the boot sequence was very lengthy. That had been going on for about a week before I started "experimenting" with Win 7 and Ubuntu.

---

### Post by T-n-T Handywork on 2009-08-24
Just an update... This weekend, I assembled some test systems. What worked for me was to dual boot was to install Windows 7 by only allowing it to partition as much of the hard drive as I wanted for Win 7. I then installed Ubuntu by selecting to manually set partitions. I set the partitions, installed Ubuntu 9.04 and rebooted to find GRUB ready to select between the two. I got courageous and tried my first triple boot (XP, Win 7, Ubuntu 9.04) after reading other posts for ideas. The solution that worked was to first install XP, then Windows 7. I booted that to check it and found that the Win 7's boot loader allows you to select between Win 7 and an older Windows operating system (ie. XP). I then installed Ubuntu 9.04. Note: Each install, I only partitioned the area intended for the specific OS. After installing Ubuntu 9.04, I was greeted by GRUB with the selections for Ubuntu or Vista loader (aka) Windows 7 boot loader. When I selected the Vista loader, it took me to the screen I had seen earlier allowing a choice of which Windows version to start. It was challenging to figure out as a novice, but the benefits outweigh the time spent. I have programs from XP that don't function in Win 7, I'm just testing Win 7 (not sold yet), and of course the stability, security, and functionality of Ubuntu. My hat is off to those who participate in making Ubuntu an awesome alternative to Windows or Mac.

---

### Post by presence1960 on 2009-08-24
Sounds like you did an excellent job on that multi OS boot installation. Enjoy Ubuntu!

---

### Post by T-n-T Handywork on 2009-08-24
Thank you! Hope it works for others. It's nice to have options ;)

---

