---
title: "which integrated wifi card?"
date: 2005-11-28
forum: Hardware &amp; Laptops
---

### Post by kreso on 2005-11-28
Which wifi integrated card works best in Linux? Intel Pro Wireless?

---

### Post by unkemptwolf on 2005-11-29
Yes! I have an Intel 2195ABG I bought off NewEgg for $40, and it works like a charm. It is always detected and installed on startup, and I've yet to have issues with it in the year I've been using it. Highly reccomended.

---

### Post by jakev383 on 2005-11-29
[QUOTE=kreso]Which wifi integrated card works best in Linux? Intel Pro Wireless?[/QUOTE]

I had an Intel Pro 2200B/G that worked, but whenever I did a large file transfer (FTP, downloading via HTTP, whatever) it would hang, drop connection, find it again after 20-30 seconds which of course killed my transfer.  I tried several of the solutions suggested on the forums, but ended up killing the wireless drivers completely.  I put the Dell TrueMobile (Broadcom BCM4401) in and went with driverloader (from linuxant.com after banging my head against the wall with ndiswrapper) and have not had a problem since. Sure, I had to pay $20 for driverloader, but I donate money to GNU projects anyway.

---

### Post by jwolf on 2005-11-29
[QUOTE=jakev383]I had an Intel Pro 2200B/G that worked, but whenever I did a large file transfer (FTP, downloading via HTTP, whatever) it would hang, drop connection, find it again after 20-30 seconds which of course killed my transfer.  I tried several of the solutions suggested on the forums, but ended up killing the wireless drivers completely.  I put the Dell TrueMobile (Broadcom BCM4401) in and went with driverloader (from linuxant.com after banging my head against the wall with ndiswrapper) and have not had a problem since. Sure, I had to pay $20 for driverloader, but I donate money to GNU projects anyway.[/QUOTE]

I think the drivers for the 2200 are much better now. Heck, even kismet works! I am impressed with the stability of the current drivers for that chipset. I am sitting on a wifi network right now using my Intel 2200BG typing this post :D

---

### Post by injectionpa on 2005-11-29
Stick with a mini that doesn't use ndiswrapper. Although a good program has it's limitations. I have one of many BCM4306,, dell 1350 and it works with ndiswrapper without a problem however kismet doesn't like ndiswrapper. 

Depends on what you want to do with the card. Just wireless a link for home office school no problem. If you want more flexability then go with a card that has an open source driver. ie prism, orinoco, realtek.

check out this site for some ideas.

[http://www.seattlewireless.net/index.cgi/HardwareComparison](http://www.seattlewireless.net/index.cgi/HardwareComparison)

---

### Post by mips on 2005-11-30
Just a word of warning. If you have a newer HP or IBM laptop you will NOT be able to install a card that was not supplied by HP or IBM. They whitelist the cards in the BIOS and only cards supplied by IBM & HP will work on their respective machines. You will notice that a card from IBM/HP costs twice the price of a genuine Intel card. Just a money making scheme.

The **good news** is that their are are hacks around this problem. The first method is to write to the cards eeprom and change the vendor ID and this works on all machines as long as the card is an INTEL chipset based card!!! The second method only works on some IBM machines and involves editing the whitelist in the laptop BIOS/eeprom.

I dont know which other vendors follow the whitelist procedure.

---

