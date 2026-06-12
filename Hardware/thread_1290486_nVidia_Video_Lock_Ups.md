---
title: "nVidia Video Lock Ups"
date: 2009-10-13
forum: Hardware
---

### Post by Stormspace on 2009-10-13
A few weeks ago I bought this barebones PC from Tigerdirect.
> (Visionman Intel Pentium Dual-Core E2180 / Socket 775 / 2GB DDR2-800 / 10/100 LAN / 6-Channel Audio / Flash Media Reader / 585 Watts / Barebones) 

It has this mobo:
> Asus P5N73-AM Motherboard
Based on the NVIDIA GeForce 7050 chipset, it supports DDR2 memory up to 4GB, PCI-e x16/x1, SATA2 with RAID, NVIDIA GeForce 7050 Graphics, 8-channel high-definition audio, and 10/100 LAN. And this sophisticated motherboard supports Windows Vista Premium, HD-DVD, Blu-Ray, and HDCP.

- Socket: 775
- Chipset: NVidia Geforce 7050
- Integrated 8 Channel High Definition Audio
- Supports dual channel DDR2 800/667/533/400 DIMMs
- 1 x PCI-E x 16 / 1 x PCI-E x 1/ 2 x PCI
- 10/100 LAN
- 4 x SATA 3Gb/s
- RAID 0,1,0+1


I've been using it with 9.04 and as long as I don't ask it to do anything that uses the 3D acceleration it's fine. However if I try to use anything 3D it will sometimes lock up hard and force me to hit the reset button. 

I've resisted installing Windows to see if the same thing happens, but wanted to ask here if anyone had any suggestions.

---

### Post by NoaHall on 2009-10-13
Have you made sure your graphics card driver is installed? (System -> Admin -> Hardware drivers

---

### Post by Stormspace on 2009-10-13
Yes. I enabled the restricted drivers for the card.

---

### Post by Stormspace on 2009-11-10
Since I was having a hard time with the 3D video I purchased an nVidia 8400GS card to replace the onboard card. Running that card caused the lock ups as well, so I decided to install Windows and troubleshoot a possible driver issue. I was still getting the lockups and they are worse. So that means hardware. Couldn't be the Video card since I replaced it, but it could be the shared memory that the onboard video is using, so...

I thought I had done this, but last night I reseated the RAM and left the machine running all night. No lock ups. Before it wouldn't last 2 hours with out locking up. For now it looks like it's resolved. I'm not done yet, since the machine was off for several hours and I'm going to see how it does when it's hot. 

Bottom line, I had to install Windows to address this issue and now that I've discovered the same thing was happening in Windows I can rule out software. So it's likely just the memory issue.

Ubuntu 9.10 still won't install from the live CD. I was waiting until I resolved my lockups before trying the alternate install disk, so hopefully that will work.

---

### Post by Stormspace on 2009-11-23
Turns out the issue isn't with the memory. I've RMAed the mobo and should be getting another any day now.

---

### Post by Stormspace on 2010-01-04
Ha! No love for the new mobo. Still problems with the lockups. Long story short, after swapping the mobo, getting some new thermal paste and testing again with the same results. I replaced the RAM which had tested OK. No more lockups. Going on three weeks with out an issue.

PS: Haven't been able to reinstall Ubuntu yet, apparently my TDK DVD drive isn't supported. The install fails at some point when the installer can't find the drive.

---

