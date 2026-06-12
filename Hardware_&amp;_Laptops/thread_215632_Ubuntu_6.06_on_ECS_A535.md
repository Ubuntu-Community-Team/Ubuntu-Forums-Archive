---
title: "Ubuntu 6.06 on ECS A535"
date: 2006-07-14
forum: Hardware &amp; Laptops
---

### Post by plamen5rov on 2006-07-14
I just LOVE Ubuntu and the previous Breezy version was working fine on my ECS A535 laptop. I have waited for the new Dapper Drake so long that I decided to make a clean frash install instead of upgrade, so I formated the whole HDD and put the Live CD in but it only led to showing just a mouse cursor at the stage of the graphical interface and that's all.

I tried installing from the other (not live) CD but again it would only install in text mode and wouldn't start the X-system...](*,) 

My laptop specifications are as follows:

Processor    On board 462pin CPGA mobile AMD processor 1.2 GHz with PowerNow!TM technology, FSB200MHz 
 
Core Logic    SiS 740+ SiS 962L 
 
Memory    On board 128MB DDR RAM 
 
Expansion 1 slot of 200pin DDR SO-DIMM DDR Module, 640MB total memory capacity. 
 
Supports DDR200 / DDR266 module  
 
LCD Display    14.1" XGA / 15" XGA (1024 x 768) TFT LCD display 
 
Video & Graphics    High performance 256bit 3D graphic engine, up to 143MHz 3D engine clock  
 
Shared memory 16/32/64MB DDR (user adjustable in BIOS, 32MB as default) 
 
Hard Drive    2.5" 9.5mm height, ATA 33/ 66/ 100 support 
 
Optical Drive    CD-ROM, DVD-ROM, Combo Drive (DVD-ROM + CD-RW), DVD Dual (DVD+/-RW) 
 
Pointing Device    Synaptics touchpad with 4 way scrolling button 
 
Audio    AC'97 2.1 compliant, SPDIF out, 5.1 channel support 
 
BIOS    Support PnP, Master Password 
 
Bootable from USB FDD and Optical Device 
 
Communication    802.11b WLAN 
 
  Built-in MDC V.90 56Kbps Fax/Modem 
 
  10/100/1000Mbps Gigabit Ethernet on board 
 
USB Connector    Four USB2.0 ports, up to 480Mbit/s 
 
 

Meanwhile, I'd installed MEPIS on it and it works just fine, but I still want my Ubuntu on it!:rolleyes: 

Can anyone give me a hand or at least a clue?!

---

### Post by plamen5rov on 2006-07-15
Come on, guys! Don't dissappoint me with this silence!:-k

---

### Post by Hal58 on 2006-07-22
Install Dapper (6.06 LTS) as you say that you've done.  I had Breezy installed on one as well, and converted it to a fresh Dapper install (from the Live CD) with no problems.  If all you get is the X cursor, then go to a real terminal (with Ctrl-Alt-F1 thru F6), log in and review the /var/log/Xorg log file to see what went wrong.  Then you can try editing /etc/X11/xorg.conf to fix the problem.  When finished, you can go back to the graphical session with Ctrl-Alt-F7 and kill X with Ctrl-Alt-Backspace.  When it restarts, see if you improved things.

BTW, I have found that the 'athcool' program really helps this computer stay out of the highest fan speed (where it sounds like a jet turbine) when the Cpu is not completely occupied.  Another thing that helps is to set the screensaver for a blank screen to keep the system from overheating when the screensaver comes on.

On the down side, there is still no audio volume control in alsa.  Good Luck.
Hal

---

