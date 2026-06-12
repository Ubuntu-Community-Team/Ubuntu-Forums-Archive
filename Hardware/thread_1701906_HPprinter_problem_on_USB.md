---
title: "HPprinter problem on USB"
date: 2011-03-07
forum: Hardware
---

### Post by mike64485 on 2011-03-07
I've had this computer for several months and all has been well until this evening. I have an old but VERY reliable, lightly used HP-5p printer attached with a generic parallel to USB converter. Suddenly this evening it won't print. I've tried the solutions suggested on various threads on the forums but nothing seems to work. The print job spools but never gets sent to the printer. 
The printer is not being found. :confused:
I have reinstalled hplip, etc, but no joy. Changed the USB cables around, etc., but no joy.
The printer is powered up and readily prints its test page. 
I've mucked with this for several hours now. I'd like advice on uninstalling CUPS, hplip, hplip-gui, etc, etc. to the point that I can reinstall everything dealing with 'print' and start fresh.
Anyone?

Many thanks in advance!!:)

PS -- Oh...it's 3:00 AM here. My wife wanted her bank statements last evening. I'm headed out to the doghouse now for a nap.

Mike

---

### Post by nomko on 2011-03-07
First things first: Does your computer see your printer? Open a terminal and type in: **lsusb[/] and put the output here. And also type in [b]lspcip** and put the output here.

---

### Post by mike64485 on 2011-03-07
I tried   '**[b]lsusb[/]**' and got "no such file or ...."
Then I tried just '**lsusb**' and got:

[INDENT]> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 050d:0002 Belkin Components 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 058f:6362 Alcor Micro Corp. Hi-Speed 21-in-1 Flash Card Reader/Writer (Internal/External)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I tried '**lspcip' **and got a suggestion to try '**lspci' **which got:

> 
02:00.0 Ethern00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 1
00:1c.2 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Root Port 3
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 SATA controller: Intel Corporation 82801JI (ICH10 Family) SATA AHCI Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controlleret controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

Is this the output you want?  


[/INDENT]

---

### Post by nomko on 2011-03-07
> **mike64485 said:**
> I tried '**[B]lsusb[/]**' and got "no such file or ...."[/B]
**Then I tried just 'lsusb' and got:**
 
My mistake. It is indeed lsusb [/] should be [/ b] (no spacial between / and b). This makes lines/words bold.
 
> 
Is this the output you want? 

 
Yes, especially the first one interested me the most. In that list your HP printer is not shown. Or you did the command with the printer turned off or the printer was turned on and no cable connected. Can you tell me if the printer was turned on or off when you entered the command **lsusb**.

---

### Post by mike64485 on 2011-03-07
The cable is solidly connected and always on. I leave it on even when the system is shut down because of the warm-up time when the printer is cold.

Thanks!

Mike

---

### Post by nomko on 2011-03-08
Go to this page and check wether the proposed driver will work for you:
[http://www.openprinting.org/printer/HP/HP-LaserJet_5P](http://www.openprinting.org/printer/HP/HP-LaserJet_5P)
 
But looking at the output of lsusb and your explanation that you did it with the printer connected and turned on, it looks more like a hardware issue to me.
 
 
Maybe this can be usefull too:
[http://ubuntuforums.org/showthread.php?t=1701547&highlight=laserjet+5p](http://ubuntuforums.org/showthread.php?t=1701547&highlight=laserjet+5p)
[http://ubuntuforums.org/showthread.php?t=1689460&highlight=laserjet+5p](http://ubuntuforums.org/showthread.php?t=1689460&highlight=laserjet+5p)
 
[http://ubuntuforums.org/showthread.php?t=184838&highlight=laserjet+5p](http://ubuntuforums.org/showthread.php?t=184838&highlight=laserjet+5p)

---

### Post by mike64485 on 2011-03-09
Well.... Thanks nomko for your effort. I guess I will check the cable and sockets again. I really hate to give up this old printer. It has been very reliable and useful until now.

I will leave this thread open for a time to see if anyone else has a suggestion

Mike :( --sad again

---

### Post by mike64485 on 2011-04-18
Broken cord. 
My wife ran over the cord while vacuuming, breaking it at the connector. New cord INSTANTLY solved the problem. Less than $10 fix.
Much embarrassment!

Mike

---

