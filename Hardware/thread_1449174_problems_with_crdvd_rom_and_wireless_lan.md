---
title: "problems with cr/dvd rom and wireless lan"
date: 2010-04-07
forum: Hardware
---

### Post by GoatFeather on 2010-04-07
i downloaded ubuntu on my Compaq v5000 and everythings great besides my wireless lan isnt working and cant seem to download the driver for it and my cd/dvd rom isnt responding after i put a dvd in to test it...please help

---

### Post by gordintoronto on 2010-04-07
Most device drivers are built-in to Linux, you don't download and install them. Wireless adapters are the weakest part of this.

The Compaq V5000 is a whole family of products. If the wireless adapter is built-in, it is probably a "pci" device. Run Accessories/Terminal and enter the command:
lspci
which should produce about 20 lines of output. Near the end, it should show your wireless adapter in a line that looks like this:
03:07.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

The key word in that line is "ar2413" which identifies the device. Perhaps you could copy the entire line into a message. You might be able to use Google to to find a solution.

This thread might be relevant:
[http://swiss.ubuntuforums.org/showthread.php?t=1312325](http://swiss.ubuntuforums.org/showthread.php?t=1312325)

As for the DVD, you need to install the "restricted extras" using Administration/Synaptic. And to do that, you need to be connected to the Internet.

---

### Post by GoatFeather on 2010-04-08
thanks so much. this did the trick works like a charm now.
 
GoatFeather

---

