---
title: "Dual boot Ubuntu 64 and vista 64 issues"
date: 2009-03-10
forum: Installation &amp; Upgrades
---

### Post by Mitul on 2009-03-10
Hello all,
I'm pretty new to this game so I'll try my best to explain my issues. Also, this is my first linux install.
I just build a brand new CPU: Asus M3N78 Pro mobo, Phenom 9500(Quad), 8gb ram, XFX Geforce 9800GT, and 2x 300 SATA HDD

Ok, this is what I did in chronological order
Installed Vista 64-bit via DVD-ROM. During the install I created 3 partitions on the 1st HDD. Vista 64-bit on first partition. Most of the drivers (LAN and audio) were included with the mobo so it worked.

Problem # 1 : My graphics card is not showing me the higest resolution. Shows that it is installed in the device manager. I decided to move on from here for now...
Then I downloaded Ubuntu...desktop-amd64.iso and started installtion via usb flash drive. During installation, I installed ubuntu by deleting the 3rd partition manually, re-creating two partions including swamp area and installed it, which went fine.

Grub asked me to pick OS and I picked ubuntu and it worked...great!!! but failed to relod drivers for making "windows jiggle" under change desktop menu
Restarted back to Grub menu and picked vista
Problem 2: Vista stopped working, it asked me to repair it. I did but dosent work...

So, finally I wiped out everything and re-installed vista 64, Problem #1 still remains even after installing the current drivers from the graphics card vendor...
Basically, I need help running both vista 64 and ubuntu 64...I pretty much followed on-screen directions and like I said this is my first linux install...
Any suggestions helps since it's a fresh install

---

### Post by s.dalas on 2009-03-10
> **Mitul said:**
> Hello all,
I'm pretty new to this game so I'll try my best to explain my issues. Also, this is my first linux install.
I just build a brand new CPU: Asus M3N78 Pro mobo, Phenom 9500(Quad), 8gb ram, XFX Geforce 9800GT, and 2x 300 SATA HDD

Ok, this is what I did in chronological order
Installed Vista 64-bit via DVD-ROM. During the install I created 3 partitions on the 1st HDD. Vista 64-bit on first partition. Most of the drivers (LAN and audio) were included with the mobo so it worked.

Problem # 1 : My graphics card is not showing me the higest resolution. Shows that it is installed in the device manager. I decided to move on from here for now...
Then I downloaded Ubuntu...desktop-amd64.iso and started installtion via usb flash drive. During installation, I installed ubuntu by deleting the 3rd partition manually, re-creating two partions including swamp area and installed it, which went fine.

Grub asked me to pick OS and I picked ubuntu and it worked...great!!! but failed to relod drivers for making "windows jiggle" under change desktop menu
Restarted back to Grub menu and picked vista
Problem 2: Vista stopped working, it asked me to repair it. I did but dosent work...

So, finally I wiped out everything and re-installed vista 64, Problem #1 still remains even after installing the current drivers from the graphics card vendor...
Basically, I need help running both vista 64 and ubuntu 64...I pretty much followed on-screen directions and like I said this is my first linux install...
Any suggestions helps since it's a fresh install

Ok lets start all over again:
With these steps everything was running great for me (i have done about 5 setups in different pcs)
1.Install Windows (during installation make a partition for Win and the other leave it unallocated)
2.restart and Login in Windows and make a user (eg.ME )
3.restart and put in Ubuntu installation cd
4.make a new installation
5.at partition manager go to manual - and make an ext3 partition for Ubuntu with mountpoint "/"
6.at ntfs partition (windows) put mountpoint "/windows" DONT format the partiotion
7.make a swap partition (about the size of your ram)
8.make any other partition you want (free space etc) but if you want to be accessed by windows make them fat32 format.

At least these steps working fine for me. 

Good luck and post back for any trouble

---

### Post by Mitul on 2009-03-12
> **s.dalas said:**
> Ok lets start all over again:
With these steps everything was running great for me (i have done about 5 setups in different pcs)
1.Install Windows (during installation make a partition for Win and the other leave it unallocated)
2.restart and Login in Windows and make a user (eg.ME )
3.restart and put in Ubuntu installation cd
4.make a new installation
5.at partition manager go to manual - and make an ext3 partition for Ubuntu with mountpoint "/"
6.at ntfs partition (windows) put mountpoint "/windows" DONT format the partiotion
7.make a swap partition (about the size of your ram)
8.make any other partition you want (free space etc) but if you want to be accessed by windows make them fat32 format.

At least these steps working fine for me. 

Good luck and post back for any trouble
Thx S.dals
The install works but it's really werid and I don't quite understand what happened. You can read if you like but I'ma try fresh install all over again....

This is what happened:
I have two 300gb HDD (Sata 2 and Sata 3 under bios)

1st HDD: 
1 partition, NTFS, Vista-64 installed and working
rest of the space was unallocated
***at this point 1st hdd (1 partition rest unallocated) 2nd HDD NTFS Storage

Ubuntu install:created partion on the rest of the unallocated space on the 1st HDD, and installed ubuntu..everything installed

now when I restart it goes straight to windows and GRUB dosent load...So i thought maybe i mistakeny installed it on the 2nd HDD..

Now here's where it's confusing...Under bios if I give boot priority to Sata 3 (2nd hdd), then grub loads, ubuntu works, and vista works...
If i give boot priority to Sata 2(first HDD) then only vista loads...
If I disconnect either 1st or 2nd HDD nothing works...

WIERD!!!

Anyways, i'ma try one more time and leave one of the HDD disconnected during the entire install..lets see

---

### Post by s.dalas on 2009-03-17
sorry for the delay but i was running because i moved from the town where my university was to my home.

From what you said it seems that you have installed ubuntu on the 2nd hdd.
If you haven't done anything yet please log in through ubuntu and install gparted. (Terminal: sudo apt-get install gparted) or try from Add/Remove under Applications. There you can see everything that is happening in yours hdd.

If you have done something else and you need an advise post back for any help i can give you.

Best,
Stelios

---

