---
title: "ASUS PCE-AC51 dual band PCI-E wireless adapter"
date: 2018-09-29
forum: Hardware
---

### Post by bfloyd4445 on 2018-09-29
This pci-e WiFi adapter works right out of the box but upload speed is very slow like 100kbps. I have it installed on an asus b-450 plus MB with two hd's one with win10 pro and the other with Ubuntu 18.04lts. In windows i get 50 to 30 Mbps both ways but with Ubuntu only 6-15mbps download and 100-200kbps upload on the same network. I'm sure the issue is the Linux driver but i cannot figure out how to install the proper driver. I bought this card because it said full Linux support and there is an available driver  _PCE_AC51_10020160603 on the installation cd and asus website.
Does anyone else use this card, an if so how did you install the driver?
Thanks, I'm new to Ubuntu

---

### Post by Yellow Pasque on 2018-10-01
Please get the wireless info as instructed here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by bfloyd4445 on 2018-10-02
thanks. I did as instructed and it appeared to update a bunch of files but did not load the Linux driver for my asus pci-e PCE-AC51 wifi card. I have a cd with the driver and have also downloaded it but not sure how to manually install it. I'm Linux illiterate

---

### Post by Yellow Pasque on 2018-10-02
> It will create the file "wireless-info.txt" at the location it is run from, and depending on its size, an additional archive called "wireless-info.tar.gz". If you prefer, you can post the file directly to pastebin yourself. Sensitive information like MAC addresses and WPA/WEP keys are masked automatically.

Yes, It updates "a bunch of files", but that is not the point. We are interested in the wireless-info.txt file that is produced, which you need to post.

---

