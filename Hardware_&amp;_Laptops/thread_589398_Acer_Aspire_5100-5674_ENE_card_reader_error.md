---
title: "Acer Aspire 5100-5674 ENE card reader error"
date: 2007-10-24
forum: Hardware &amp; Laptops
---

### Post by jointstereotype on 2007-10-24
**UPDATE 2007-11-08:** After 2 weeks of null results, I've given up on the ENE card reader. LOL I went out and bought a Sandisk USB reader, and though it doesn't always show up when plugged in (lordie, another problem to have to figure out...*sigh*), it mounts / unmounts / writes / reads all my SD cards just fine, and works faster than the ENE did.

--

I recently installed Gutsy on an Acer Aspire 5100-5674 laptop, and am quite pleased with the result, despite a few configuration hurdles. The only thing I can't get to work is my ENE card reader. I heard the reader is supposedly supported in Gutsy, and indeed, where Feisty didn't even acknowledge the presence of the reader, I can now insert an SD card (2gb Kingston) and a Nautilus window will pop up, listing my files, giving proper disk usage stats, etc. However, when I try to copy files from the SD card, I get an I/O error. The SD card works just fine using the reader in my Windows XP laptop.

Anyone have any ideas on how to coerce the ENE reader into full cooperation? ;)

FYI: If it's any help, here are the relevant lspci lines pertaining to the reader:

06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

---

### Post by jointstereotype on 2007-10-25
*bump* Anyone use the ENE card reader on their Acer laptop under Ubuntu 7.10?

---

### Post by jointstereotype on 2007-10-25
Okay, I found a couple of spare memory cards and did some informal testing. The two Sandisk 256mb SD cards I tried worked beautifully. I was able to cut / copy / delete files to / from the cards without a problem. I also tried an *old* 8mb Panasonic MMC card, which worked equally as well. Lastly, I tried the 2gb Kingston SD card and I got the same i/o error as before, with a Nautilus crash, to boot.

So, it seems the reader works, but only when using certain brands - or perhaps the Linux ENE driver only supports SD cards smaller than 2gb...?

---

### Post by jointstereotype on 2007-11-07
Just a little *bump*. ;) Anyone out there...?

---

### Post by hbk_99 on 2007-11-15
Hi jointstereotype i see we have the same laptop did you have any problems with wireless conection on wire?:guitar:

---

### Post by jointstereotype on 2007-11-16
At $500, I couldn't say "no." Now I'm saying "ugh!" LOL

Wireless was tricky to set up. I didn't takes notes, but should have. I do remember trying the Ubuntu restricted drivers first, restarting, and discovering that all the local wireless networks in my area were listed, including my own, but I couldn't actually connect. I disabled the restricted driver and installed the ndiswrapper driver following [these instructions]("http://ubuntuforums.org/showthread.php?t=405990")...and i had the same problem. Somewhere along the line I restarted and suddenly my wireless network worked, and has ever since...though I don't know exactly what I did, if anything. :p

Any luck with your card reader? Have you tried any SD cards larger than 256mb in it?

---

### Post by benmca on 2008-01-14
I am successfully using a SanDisk SDHC 4GB Card with Gutsy on an Aspire 5100. b

---

