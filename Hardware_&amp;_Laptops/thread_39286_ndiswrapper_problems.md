---
title: "ndiswrapper problems"
date: 2005-06-04
forum: Hardware &amp; Laptops
---

### Post by UrbanSlayer on 2005-06-04
My laptop (an IPC TopNoteH) was running Warty up until this morning, when i decided to nuke it and install Hoary. Everything is running fine except my wireless.  I copied the driver files for my wireless card from the /etc/ndiswrapper folder before i nuked the Warty install, but now when I try to use them in Hoary, it just doesnt seem to work.

I've install ndiswrapper, run ndiswrapper -i /DRIVERFILE and this works ok, the modprobe works fine, ndiswrapper -l returns the correct results, it appears to be loading on startup from the dmesg output, yet the card does not come up, the lights do not appear on it etc.

I have got Firestarter installed, and I have told it to use the wlan0, but that hasnt helped.

ifconfig wlan0 up doesnt return any errors either.

wlan0 appears in the Network Settings screen, and I can configure it correctly (the exact same config as on Warty) and yet the card is not brought up.

Im using a bcmwl5 driver, on a Belkin F5D7010 card.  As I said, im using the same driver I used on Warty so I dont understand why it doesnt work.

Anyone got any ideas?  

Thanks

---

### Post by xristos on 2005-06-04
When you are in a place where there are APs active and you do ```
iwlist wlan0 scanning
```  does that give you a result ?

---

### Post by UrbanSlayer on 2005-06-04
No, it doesnt, but this doesnt surprise me as my AP is set to not broadcast the SSID.

---

### Post by UrbanSlayer on 2005-06-04
Ok, somehow I have now managed to get it running, it has an ip etc, my router is seeing it (Inactive though), yet I can not connect out with it.  For some reason, this was so much easier in Warty.

The whole thing appears to be configured correctly, and in a very bizarre situation, i can connect to the wireless IP when the Ethernet cable is attached, but not when it isnt (the wired and wireless connections have completely different IPs).  Something is getting confused somewhere..

---

### Post by UrbanSlayer on 2005-06-04
Ok, I have now gotten it working.  I had to install 1.2rc2 from source, and that seemed to get it all going.

Thanks

---

