---
title: "Need help with wireless!"
date: 2006-02-03
forum: Hardware &amp; Laptops
---

### Post by Cenotaph on 2006-02-03
Okay, i'm trying to make my wireless work in my college, but i can't get it to work.

first of all, i need to install the chipset (it's a nightmarish broadcom).

I've tried to use ndiswrapper and followed the HOW-TO in this forum and it apparently worked, the wireless interface appears in network configuration but i can't get no net at all. My computer is probing for available networks, and it finds a lot, but still it doesnt work.

after i followed the instructions to get Wifi working here i only got an error when i was trying to set the key for this network

iwconfig wlan0 essid e-U key 0

got this output:

Error for wireless request "Set Encode" (8B2A) :
      SET failed on device wlan0 ; Invalid argument.

And then when i use xsupplicant -i wlan0 I still can't get no net.

Any ideas what could be wrong?

---

