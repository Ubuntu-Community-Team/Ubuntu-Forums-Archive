---
title: "New Build EXTREMELY Laggy / Hanging"
date: 2015-02-18
forum: Hardware
---

### Post by Dr Spliff on 2015-02-18
So, this all happened about a year ago.  When I click the Unity icon to pop up the menu for example, it will hang and although I can move the mouse around, most of the time the window is unresponsive (and sometimes turns white).  

I determined this wasn't a RAM problem, so figured my MOBO or Processor was to blame.  I bought a brand new motherboard and processor, hooked it up, low and behold it still hangs!  OK, maybe it was the RAM, bought two brand new sticks of 1600mhz RAM (16GB, 2*8GB), still same problem.  OK, maybe my hardware setup simply has a problem with Linux.  Tried installing Windows 7, same thing happens when clicking "START" or going to view computer properties for example.  And yes, I tried installing the drivers that came on my MOBO disc, no success.  Yes, I tried downloading the updated drivers from Gigabyte, no success.  Also, Yes my bios is updated and this was the case with my last mobo as well.  

I'm sure you're thinking, well it can only be one of two things then : the Power Supply is giving off faded voltages and hangs the Hard Drive, or the Hard Drive itself is going out.  Replaced the Power Supply with a Brand New 850W ThermalTake PSU, still hangs.  Ok, it must be the hard drive.  Tried a different SATA drive, formatted and installed Ubuntu.  Hangs still.  Formatted and installed W7, hangs still. 

OK WTF, this HAS to be a problem with something in the BIOS.  When this happened to my other MOBO, I combed through the BIOS and enabled / disabled options and restarted about 200 times trying to get the problem to go away.  Same situation.  I tried messing with the "FAST BOOT" options, no success.  Made sure Hard Drive was set on AHCI.  Replaced SATA Cable.  Replaced replacement SATA Cable.  Nothing helps.  

So what gives?  Either this is a MAJOR Flaw in Gigabytes F14/F15 BIOS that it appeared BOTH the the G97 and Z97 chipsets, or I had a virus infect the BIOS of both boards from my hard drive.  This is honestly getting frustrating, I could have bought a $200 PC from WalMart that would actually function.  I have now spent $130 on a PSU and $130 on RAM in the past 2 days, and my PC is still not functioning.  I consider myself decent with computers too, and this is not my first build, so to be the point of almost giving up on basically 100% new hardware is embarrassing. 

Resource monitor doesn't show anything indicating a high load on either cores of the processor, or the RAM.  So my question remains, "What else could this possibly be?" 

Specs [CURRENT] :
-Pentium G3258 Haswell Dual-Core 3.2GHz
-Gigabyte GA-H97M-D3H LGA 1150 Intel H97 HDMI SATA 6Gb/s
-(2) PNY 8GB PC3-12800 DDR3 [16GB]
-ThermalTake - SMART Series 850-Watt ATX Power Supply
-Western Digital Blue WD10EZEX 1TB 7200 RPM 64MB Cache SATA 6Gb/s

I have my graphics card and CD-ROM disconnected, which still causes the problem to happen.  Here were my specs when happening before:

Specs [OLD] :
-Gigabyte GA-B75M-D3H LGA 1155 Intel B75 HDMI SATA 6Gb/s
-(4) Kingston HyperX 4GB 240-Pin DDR3 SDRAM DDR3 1600 (16GB)
-Rosewill RP600V2-S-SL 600W ATX12V

---

### Post by weatherman2 on 2015-02-18
Did you run Memtest to test the RAM?  Let it run for an hour?

Did you check for a firmware (BIOS) update from Gigabyte?

Do you have the same "hanging" when you boot a Ubuntu live USB vs. running an installation from a hard drive?

---

### Post by Dr Spliff on 2015-02-18
I tested my old RAM with Memtest and it passed just fine, but bought two new sticks anyways.  Same results.

Whether I'm running LIVE from a disc or USB, it's still laggy, which leads me to believe its a hardware problem.  All that aside, it happens just as well with Ubuntu installed on the Hard Drive.  Additionally, I have attempted to install Ubuntu to a USB Stick and have had similar results (although my USB Stick isn't USB 3.0, just 2.0).  I have also tried to install Linux Mint to a USB Drive but with similar results.  

What's irritating is the system acts like it has 512MB of RAM and a 600MHz Single Core Processor.  My specs show up as they should (16 GB RAM and 3.2GHz Dual Core), and neither of these ever get overloaded by simply opening a web browser or clicking the Unity button.  

I have the updated BIOS on my board.  This happened with my other board with the older BIOS, I updated it and it still happened, which led me to buying this board.

---

### Post by Dr Spliff on 2015-02-18
Just checked and I do have the most updated BIOS for the board from Gigabyte, version F6a.

---

### Post by weatherman2 on 2015-02-18
So the only thing that you haven't changed apparently is the CPU?

---

### Post by Dr Spliff on 2015-02-18
Nope I changed that too.  I wasn't able to find the model of my last one, although I do know it was a different socket #.

---

### Post by Dr Spliff on 2015-03-02
**PROBLEM SOLVED**

Do NOT follow the directions on GIGABYTE's website.  They state the newest BIOS, and the newest BIOS download they have available, is F2a (BETA).  
Instead, download the @BIOS application, connect to the gigabyte server through the app, and you will receive the "F4" BIOS, not otherwise available on their website.

---

