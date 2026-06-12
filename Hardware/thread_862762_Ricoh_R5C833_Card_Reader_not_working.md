---
title: "Ricoh R5C833 Card Reader not working?"
date: 2008-07-17
forum: Hardware
---

### Post by FortyCaliber on 2008-07-17
Ladies and Gentlemen - 

I recently purchased an M1330.  I have since installed (and and am now using) 8.04.1 on it.  I am conducting an experiment with myself to see if a strict Linux lifestyle (at least on my laptop) is feasible.

I've hit a snag.  In an attempt to accomplish all that I do in Windows, in Ubuntu, I have found that the SD card reader does not work.

Ricoh R5C833 Media Reader and 1394 Adapter

It should be noted that this is my first major foray into Linux.  I dabble in Backtrack when the, um, need arises, but I'm not familiar, really, at all.

When I insert the SD card, nothing shows up, anywhere.  I expected a drive icon to appear on the desktop as one does when a USB drive is inserted, but nothing shows.  

Searching the Computer shows no additional drive devices.  Synaptic Package searches yield no results for "Ricoh."

I require assistance.

Thanks

---

### Post by sergiom99 on 2008-07-17
please post the outputs of 
lspci
lsusb

good luck.

---

### Post by FortyCaliber on 2008-07-17
This is the pertinent info concerning Ricoh.  It seems I had the controller model wrong, but it seems to be recognized, right? 

LSPCI
> 03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)


LSUSB
> Bus 007 Device 003: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 004: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


---

### Post by sergiom99 on 2008-07-18
well, its detected and it worked out of the box in mine.
But theres no linux support for Sony MemorySticks yet.
Is that the type of card you're using?

---

### Post by FortyCaliber on 2008-07-18
No, I am using SD (who uses Memory Stick?)

I tried to different cards and when I insert it, nothing happens.

Where should I be looking?

---

### Post by sergiom99 on 2008-07-18
Sony cameras use MS.
Sorry, thats the only one I have. And I have to read them in WinXP anyway.

Did you find anything searching the whole forums?

---

