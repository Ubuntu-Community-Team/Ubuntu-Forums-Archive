---
title: "Trying to install a 2nd video card (Levono ATI Radeon X1300) for use with third monit"
date: 2013-08-16
forum: Hardware
---

### Post by Joe_DePalma on 2013-08-16
[TABLE]
[TR]
[TD="class: votecell"][/TD]
[TD="class: postcell"]                Here is my situation - I am running Ubuntu 12.04 LTS 32 bit  on an IBM T60 laptop (for interested parties: Intel Core 2 Duo T7600  2.33 GHz, 4 GB RAM) and currently have it docked in the Lenovo 2503  Advanced Dock.  I do this to run two monitors (the dock has 1 DVI and 1  VGA out).  The dock has a PCI-E(x16) slot to add a second video card so up to  4 monitors can be used.  After a little digging, I found that IBM says  to use the Lenovo branded ATI X1300 Radeon 256 MB card, so I went on eBay and  bought a brand new card for $15.  I installed it, and the third monitor  did nothing - says "Cable not connected"


  I have been trying to figure this out now for a couple of days.  I am  using the open source radeon drivers.  I had tried to use the ATI  drivers but that got me nowhere.  When I run lspci, here is  what I get:

  jdepalma@jdepalma-ThinkPad-T60:~$ lspci | grep VGA
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI]  RV515/M54     [Mobility Radeon X1400]
0c:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV516 [Radeon X1300/X1550 Series]
  Mobility X1400 is the GPU on my motherboard (Intel 945GM chipset) and the X1300 is the  Lenovo branded card I put in the Advanced Dock.  What does the 0c:00.0 mean?   This is weird since the PCI card is detected but when I went to the  system settings there was nothing recognized (monitor or card). 

  I tried to install the ATI proprietary drivers (fglrx and amdccele) but it made my  laptop a wee bit unstable.  The radeon open source driver supports both  cards AFAIK.  I'd like to be able to run a third monitor using the X1300  if possible.  Anyone have suggestions?  Thanks in advance.

      
[/TD]
[/TR]
[/TABLE]

---

