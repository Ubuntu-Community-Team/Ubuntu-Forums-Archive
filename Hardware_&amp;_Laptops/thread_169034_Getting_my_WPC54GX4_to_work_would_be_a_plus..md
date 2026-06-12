---
title: "Getting my WPC54GX4 to work would be a plus."
date: 2006-05-01
forum: Hardware &amp; Laptops
---

### Post by The DCG on 2006-05-01
So, I'm a first time user (newbie!!) for Linux, and after FINALLY getting it installed on my laptop- by dint of changing the RAID system to SATA- I am trying to get my Wireless card working.  Unfortunatly, I didn't get any hits on a search so I guess perhaps I'm one of the first ones to try running this card?

Card is Linksys WPC54GX4 - the one with SRX400 and MIMO, which is why I'm loathe to just try another driver.  I get green lights on power and link the moment I plug it into the PCMCIA slot.  I DID try using ndisWrapper, as far as I understood it, but I would get 'driver present' without 'hardware present;' and no message in the system log as to the driver being loaded.  Any suggestions beyond beating my head in to the wall are appreciated.

-Cat, Avatar for the DCG

---

### Post by The DCG on 2006-05-03
Alright, an update.  I found out that for the MIMO support, I probably needed a recent build of ndiswrapper to even TRY and get it working.  And, since I have internet access only through other comps, I had no luck figuring out how to install the stuff (like dh-make) to compile the new ndiswrapper with my linux.... /sigh

So I decide to take a step back.  I have access to a WPC11 v4, which, according to the WIKI, works fine once you've ndis-ed it with the correct drivers, which they link.  "Alrighty!"  Says I.  And thence download the drivers, do a fresh install of 5.10 and try it.  The only thig I did was activate the ndiswrapper-utils package from within Synaptic.  So I run the ndiswrapper, and lo and behold, I get 'driver installed' but no detection of the hardware.

I did check device manager, several times, to no avail.  I was thinking it may be a failure somehow to detect what's IN the PCMCIA slot.  Here it the output of lspci, with the 'driver loaded' and the WPC11 plugged in (and lit).
the-dcg@Gaav-Flare:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 915G/P/GV Processor to I/O Controller (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 915G/P/GV PCI Express Root Port (rev 04)
0000:00:1b.0 0403: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
0000:00:1d.0 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
0000:00:1d.1 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
0000:00:1d.2 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
0000:00:1d.3 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
0000:00:1d.7 USB Controller: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev d3)
0000:00:1f.0 ISA bridge: Intel Corp. 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
0000:00:1f.1 IDE interface: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
0000:00:1f.3 SMBus: Intel Corp. 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
0000:01:00.0 VGA compatible controller: nVidia Corporation: Unknown device 00c9 (rev a2)
0000:0a:00.0 CardBus bridge: Texas Instruments PCI1410 PC card Cardbus Controller (rev 02)
0000:0a:01.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
0000:0a:02.0 RAID bus controller: Promise Technology, Inc. PDC20378 (FastTrak 378/SATA 378) (rev 02)
0000:0a:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

As you can see, I don't see a thing about the card.  I was seeing that it might have something to do with the system itself.  SO, straight from the invoice.
System Specs:
Alienware Area-51m 7700 17" SXGA+W/CAM LCD Display
P4 3.8GHz 670 2MB FSB LGA775 Tray Ver.
PDP 512MB DDR2 PC4200 SO-DIMM CL4 (X4)
D900T Nvidia Ultra 6800FX Go with 256MB
Hitachi Notebook 100GB 5400 RPM HD (x2)
REV 3 8X DVD+/-RW Panasonic
24X RV3 DVD CD-RW Combo Panasonic

Err... I would think none of the rest matters.  I hope.  If not, I can find it out.  Here is hoping that this helps with the ongoing troubleshooting.  I'd REALLY like to be able to connect to the intertron on something othet than someone elses laptop.  I'm SURE the answers are in here, ot the WIKI somewhere, but I've had no luck finding them.  Here is hoping y'all can help.

Thanks in advance.  Abject thanks, if it works.  /laugh

---

