---
title: "Acer 5570 Card Reader Not Working"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by frank26080115 on 2007-09-23
I have a sony memorystick pro duo to test it with, and it doesn't work.

lspci shows:

0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

dmesg shows (after I inserted the card):

tifm_core: MemoryStick card detected in socket 0:0

dmesg after I remove the card:

tifm0 : demand removing card from socket 0:0

The other bad news is, it doesn't work in vista either.

---

### Post by Z_Cee on 2007-09-24
I have a 5570Z and a letter I was emailed said  it was a non-commital letter that said absolutly nothing. But, it is a repsonse so that they can't be sued because they ignored a warranty issue.

I'm in the process now to where I sent several request for Acer to send me a replacement XP system for the Vista system they installed. 

I worked for close to an hour on getting the bios to accept booting CD's first. The original instructions they gave was a fairy-tell. IN otherwords nothing but lies.

---

### Post by ergosteur on 2008-01-21
My 5570Z came with Vista. My card reader works under XP and openSUSE. I get the same dmesg output when I insert a card:
[  355.116000] tifm_core: MMC/SD card detected in socket 0:1
[  355.232000] mmcblk0: mmc0:0002 SD2GB 1955328KiB 
[  355.232000]  mmcblk0: p1
[  429.868000] tifm0 : demand removing card from socket 0:1

---

### Post by frank26080115 on 2008-01-21
SD cards work, but not xD or Memory Sticks

---

