---
title: "Printing to Laserjet 6P using USB-to-parallel cable"
date: 2017-04-17
forum: Hardware
---

### Post by selvaswami2 on 2017-04-17
Hi;

Vanilla install of Ubuntu 16.04 on a Dell Optiplex 390. Went to install my reliable old HP 6P laser printer only to find my new box has no parallel port. Sooo . . . bought a USB to parallel cable off eBay, hooked it up, and have tried everything by way of online advice to get the printer to accept jobs, but no luck.

It might be the generic cable I bought. It might be me not telling Ubuntu where it is correctly.

Maybe I need to put a PCI card in this PC to give me a parallel port. Maybe I need to buy a USB printer.

My home network runs some Ubuntu and some Windows boxes, but maybe I can run a Wi-Fi printer for everyone.

Any advice on the best course to take is much appreciated.

Thanks,

Selvaswami

---

### Post by gsahli on 2017-04-17
A USB-to-parallel cable has a small circuit called a data shifter (usually in the parallel plug). There are lots of variations in these, but they usually provide one-way comm only. Drivers for HPs usually rely on two-way comm, like from the parallel port. You can try other brands, or...
Here's how I solved that - buy a cheap parallel ethernet "print server" and put your printer on the network. (Wifi print servers aren't as cheap)

---

### Post by Autodave on 2017-04-17
If it is time to replace that printer, think about staying with HP since they have the least problems setting up.

---

### Post by pdc on 2017-04-17
like here [https://forums.linuxmint.com/viewtopic.php?f=51&t=243042](https://forums.linuxmint.com/viewtopic.php?f=51&t=243042)

and here ? [https://forums.linuxmint.com/viewtopic.php?f=51&t=242922](https://forums.linuxmint.com/viewtopic.php?f=51&t=242922)

---

### Post by Autodave on 2017-04-17
I didn't say they were simple every time.  However, I personally have never had an issue with an HP. I currently have 4 machines running through printers: all HP. 3 are corded to the printers, one is wireless. The wireless one took me all of about 3 minutes to set up. (MFP M277dw).

Now having said that, setting up the scanning portion can be a lot more fun. Thankfully, the 2 corded machines had no issue. The wifi one does, but it has a very nice USB port on the front panel and it is a cinch to scan to a USB stick.

---

### Post by pdc on 2017-04-17
thanks Dave; hopefully all printers will get more easy; 17.04 continues to work on making things easier [http://www.zdnet.com/article/ubuntu-17-04-the-bittersweet-linux-release/](http://www.zdnet.com/article/ubuntu-17-04-the-bittersweet-linux-release/) 

"The new desktop also supports the new "driverless" printers. These printers include IPP Everywhere and Apple AirPrint printers. When you're using these printers over either an USB or network connection they should setup automatically. Canonical describes the process "as easy as connecting a USB stick.""          that should all help; Canon now have one driver that seems to be power all their new releases ...... you just download that; and gutenprint seem to be able to support all the new printers very easily

---

### Post by selvaswami2 on 2017-04-21
Thanks to everyone for your excellent suggestions. I'm going to put a PCI parallel card in this box, but it's worth it to the other users on this network to get a more modern printer, and put it on an Ethernet adapter.

---

