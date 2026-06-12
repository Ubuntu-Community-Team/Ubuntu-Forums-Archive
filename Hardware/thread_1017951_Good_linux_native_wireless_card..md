---
title: "Good linux native wireless card."
date: 2008-12-21
forum: Hardware
---

### Post by jesermay on 2008-12-21
Does anyone know of a Wireless card that has native drivers for linux? I currently have a [EW-7728in]("http://www.edimax.com/en/produce_detail.php?pd_id=225&pl1_id=1&pl2_id=44") Which I just can't seem to get to work with linux, if I could I would love to because its performance is awesome. If anyone knows how to get the EW-7728in to work on ubuntu 8.10 please tell me. 

Anyway, the reason for me mentioning that wireless card is because I would like to find a wireless card which will run natively with linux/windows but has the same performance or greater of the EW-7728in.

Thanks,

Jeremy Reid

---

### Post by jesermay on 2008-12-22
bump

---

### Post by Yellow Pasque on 2008-12-22
Before you rush out to buy another card, what chipset does your current wireless card have? (lspci or lshw should show you info)
```
sudo update-pciids
lspci | grep Ethernet
sudo lshw -C network
```

EDIT: nvm, I see this: [http://ciaranm.wordpress.com/2008/07/14/edimax-ew-7728in-80211n-ralink-rt2860-with-linux-2626/](http://ciaranm.wordpress.com/2008/07/14/edimax-ew-7728in-80211n-ralink-rt2860-with-linux-2626/)

---

