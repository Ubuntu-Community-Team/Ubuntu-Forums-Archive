---
title: "Squeeze :  No Audio from SBLive?"
date: 2010-10-22
forum: Hardware
---

### Post by AoSteve on 2010-10-22
Alright...I do officially give up on the  ...insert linux distro name... forums..  Almost no use...

Alright here is the issue..  I can't get a lick of sound of of either of my sound cards.   I know the reason for one..  PCI-e X-Fi Xtreme Audio (POS won't ever be compatibly with x64....  maybe one day doubtful though..)   Second is an OLD PCI Sound Blaster Live! Platinum.  No other distro has ever given me any trouble...

Quick snippet of lspci:

```

03:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 8800 GTS 512] (rev a2)
07:05.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 05)
07:05.1 Input device controller: Creative Labs SB Live! Game Port (rev 05)
09:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
0a:00.0 SATA controller: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
0a:00.1 IDE interface: JMicron Technology Corp. JMB362/JMB363 Serial ATA Controller (rev 03)
0b:00.0 PCI bridge: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG PCI to PCIe Bridge
0c:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```

Ok; so we know it's there.. the EMU10k1 chip is well supported with Linux.. so why can't I get any sound from it?  I've tried using *sudo alsamixer* to change the output to the SBLive.. which on Ubuntu works... Mint.. works...  this works that works.. but not my install of LXDE/Squeeze (debian)...    Any ideas?   Just before we start any "Is the card bad?"    No... My two installs of Ubuntu, and my install of FreeBSD works perfect with the SBLive and took nearly no time to change over to the SBLive and aplay works...  Hrm...

---

