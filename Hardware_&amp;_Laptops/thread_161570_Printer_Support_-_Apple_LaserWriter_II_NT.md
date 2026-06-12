---
title: "Printer Support - Apple LaserWriter II NT"
date: 2006-04-17
forum: Hardware &amp; Laptops
---

### Post by Kuprin on 2006-04-17
Yes, this old relic is my NEW printer...need some help making it work. I read the tutorial on AppleTalk printers and should be able to configure Netatalk without difficulty. My problem is, I can't try that until I get some pinouts for a DB25 cable that'll connect a PC to this beast, and I need to know if Netatalk (or Ghostscript for that matter) will handle a printer this old!

Also...don't suggest I just hook it up to my router via Ethernet. It doesn't *have* Ethernet. :eek:

---

### Post by 2FishInATank on 2006-04-27
I've also got an old LW II NT which I'm hoping to hook up with Breezy, there's a manual available from the Apple site [http://manuals.info.apple.com/Apple_Support_Area/Manuals/printers/0303215LWIINTNTX.PDF]("http://manuals.info.apple.com/Apple_Support_Area/Manuals/printers/0303215LWIINTNTX.PDF")

In the 'real' manual that came with mine it describes the cable required as a 25 pin RS-232 and gives the pinout for the printer's port as:
> 
**Pin**____________**Circuit**____________**Description**
--------------------------------------------------------------
1 or 7*__________SGnd____________Signal ground
2*______________Txd_____________Transmit data
3*______________Rxd_____________Recieve data
4_______________Rts_____________Request to send
5_______________Cts_____________Clear to send
6_______________DSR____________Data set ready
8_______________DCD____________Data carrier detect
20______________DTR____________Data terminal ready
22______________Ring____________Ring indicator

* Your LaserWriter II needs only pins 1 (or 7), 2, and 3, but a connected device may require others. For example, to exchange information with an MS-DOS computer using the DSR/DTR handshake, pins 6 (DSR) and 20 (DTR) on the RS-232 porst of the Laser Writer II must be connected to their counterparts on the serial porst if the MS-DOS computer


Hope this helps!

---

