---
title: "HELP!!! dell inspiron 5150 and netgear wg511v2"
date: 2009-09-21
forum: Hardware
---

### Post by theplan on 2009-09-21
i'm a total newbie to Ubuntu and everything seems to be working fine and kicking *** except for this wifi card
i have no idea how to get this to work
i've looked at allot of information on this and all of it looks like greek to me.
i need the most basic step by step instructions on this you can give me
you are all much more well equipped than me at dealing with this

---

### Post by tom66 on 2009-09-21
Go to Applications > Accessories > Terminal. This is the terminal which lets you issue commands. At the terminal you type commands and press enter to execute them and get potential output.

Type: "lspci" without the quotes, press enter. Paste the output here (Ctrl-Shift-V).

---

### Post by theplan on 2009-09-21
00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:01.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
02:04.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:04.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)

---

### Post by theplan on 2009-09-23
anybody?

---

### Post by theplan on 2009-09-23
could i please get some help?
i would love to keep using ubuntu but if i cant get this card to work i'm going to have to scrap it and go back to windows because it would become useless at work
i did some more looking around and i saw that some suggested using ndiswrapper so i installed it
i don't have the driver cd and i have no idea how to get the .inf file for the driver out of the downloadable .exe from netgear
i tried loading the exe with wine and i looked for the .inf file in there 
i tried to load it using "windows wireless drivers" but i load it in and it tells me it's not a valid driver
can anybody help me out?

---

### Post by theplan on 2009-09-23
Problem solved!!!!
After allot of looking around and several broken objects in my immediate area i have found a solution [http://robotsaregodless.blogspot.com/2008/06/ubuntu-wg511-v2-ndiswrapper.html](http://robotsaregodless.blogspot.com/2008/06/ubuntu-wg511-v2-ndiswrapper.html)

this makes it as easy as it gets

for noobs just forget about the terminal for this and download the files he tells you to
then go to system, administration, then wireless windows drivers
load the file called "mrv8335.inf" and it should start working right away

(side note)
there should be some sort of way that ubuntu could simplify the process in the future by making some sort of downloadable fix with synaptic

---

