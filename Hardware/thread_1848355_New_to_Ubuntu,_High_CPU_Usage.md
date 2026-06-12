---
title: "New to Ubuntu, High CPU Usage"
date: 2011-09-22
forum: Hardware
---

### Post by NohOne90 on 2011-09-22
I recently installed Ubuntu 10.10 on an old desktop.

HP Pavilion 522n

All specs were original, with the exception of a sound card because the driver to the internal one was deleted and the company we took it to decided to rip us off. (I was 10 and knew very little about computers at the time so I didn't just look up the driver myself)

As the original memory was 256MB of DDR SDRAM I had to upgrade this as it is the bare minimum for 10.10. This system is now running on 1GB (2x 512 RAM cards)

My CPU usage is at a constant 95-100%. I have tried finding the drivers using the "ADDITIONAL DRIVERS" tool under system and it only says "No proprietary drivers are in use on this system" and does not give me ANY other information except the HELP button and CLOSE button. I was looking for this as I had heard from a few people that it could be that I don't have drivers installed on the computer (which is still quite possible)

In the terminal, typing lspci gives the following information

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:0a.0 Multimedia audio controller: Avance Logic Inc. ALS4000 Audio Chipset
02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)

When I open the SYSTEM MONITOR the following items are the only active processes

kacpi_notify                     . . . This process ranges from the 30% to the 95% range at times
xorg                                 . . . This is intermittent, but takes up 95% to 100% when it is active
gnome-system monitor   . . . I expect this as it's a process I have open - uses about 4% to 7%
update-apt-xapian-index . . . I expect this too as I have not terminated the update window. It runs at 1%
firefox-bin                        . . . Also intermittent, this often takes up about 50% when it is active

In the SYSTEM MONITOR under the SYSTEM tab it shows the following

UBUNTU
     Release 10.10 (maverick)
     Kernel Linux 2.6.35-22-generic
     Gnome 2.32.0

HARDWARE
     Memory: 1000.2 MiB
     Processor: Intel (R) Celeron (R) CPU 1.8 GHz

SYSTEM STATUS
     Available Disk Space: 50.4 GiB



Another strange thing (or at least I think it's strange) is that my Memory usage is relatively low. On average only 22% is used by programs, and 31% is used by the cache. But from the time of startup the CPU usage is always at 95% or higher. The sound doesn't work on either installed sound card (integrated or the one the other company gave us, which didn't come with a disc with the drivers on it)

Any suggestions? Where can I find these drivers and how exactly do I install them? I'm not very familiar with Linux systems although I have used Ubuntu for about a year now on my Toshiba. It is a Dual OS System with Windows 7 and has absolutely NONE of these problems... But that's also a 7 year difference in the age of the computer as well. (2001 for the desktop, 2008 for the Toshiba)

Help please! Thank you in advance!

---

### Post by .... on 2011-09-22
Try this: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver)

---

### Post by garvinrick4 on 2011-09-22
The older cpu's I have found can just be hard on cpu usage. I have had to make sure anything flash is
always ran at SD not HD and in some 240 and not anyhigher like YouTube. Can be adjusted in any running flash video in lower right of video. 
Sometimes it is just neccessary to run lubuntu which is a lighter distro. The Ram upgrade is great from 256 to 1 gig but would give lubuntu a go. That is just my opinion
on how to make you happy with machines performance. Sometimes things just get old, happens to everything even some of us users have same problem with ourselves. 
I am only 58 and I feel like I could use a new CPU. Give a lighter weight Ubuntu based distro a chance, like lubuntu.
Lots of links out there. Have a nice day.
[http://lubuntu.net/blog/lubuntu-1104-released](http://lubuntu.net/blog/lubuntu-1104-released)
[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by .... on 2011-09-22
@garvin: Use Flashvideoreplacer and you might be able to play HD stuff, especially if you have a GPU which accelerates video. The only cards that accelerate Flash video using the Adobe plugin are nvidia (only on 32-bit with binary driver).

---

### Post by garvinrick4 on 2011-09-22
> **.... said:**
> @garvin: Use Flashvideoreplacer and you might be able to play HD stuff (especially if you have a GPU which accelerates video).
I do not have a older machine available right now but when I do I will google your advice and give
it a whirl. Thanks.

---

### Post by madjr on 2011-09-22
+1 for lubuntu

also effects turn off, could help

---

### Post by NohOne90 on 2011-10-02
> **.... said:**
> Try this: [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver](https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Manually_enabling_the_Intel_driver)


This says something about creating a file for the driver configuration. How do I do this? This particular wiki is ambiguous as to how to go about this...

---

