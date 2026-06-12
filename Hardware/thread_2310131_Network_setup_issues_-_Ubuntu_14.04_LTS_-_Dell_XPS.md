---
title: "Network setup issues - Ubuntu 14.04 LTS - Dell XPS 2710 AIO"
date: 2016-01-16
forum: Hardware
---

### Post by jfaberna on 2016-01-16
My Dell XPS 2710 AIO has both Wifi and Ethernet available.  I noticed there were issues when I installed Ubuntu 14.04.3 LTS from the LiveCD image with being able to download updates when installing.  I had to enable the WPA2/AES password on the Live image for the downloads to work during install.

So now the system is installed and working, except once I boot, networking only works for a few minutes.  Once it stop, I can click on the Networking Icon on the menu bar, top right, and disconnect the ethernet and then everything works.  

I'd like to get this working with ethernet since it should be better bandwidth within my home network.  All the networking hardware works on the Windows side. (it's a dual boot system) On windows 10, it uses ethernet unless the cable is disconnected, then it switches to WiFi.  I'd like that to work on Ubuntu.

Any ideas?

---

### Post by jfaberna on 2016-01-16
Additional data:

I Clicked on the upper right Networking Icon and chose Edit Connections...    I edited ethernet to connect if available.  I edited WiFi to not connect.

Once I rebooted, I had wired ethernet for about 2 minutes, then it stopped. I can't even ping inside my home network.  

I can get networking to work by re-editing the Connections and enable both WiFi and ethernet.  The WiFi connects, but I have no networking until I click disconnect on the ethernet.

The hardware is: Qualcomm Atheros AR816x/AR817x Ethernet

---

### Post by jfaberna on 2016-01-16
Okay a bit of progress.  I found a post somewhere by some anonymous poster that there is a problem with the current Linux kernel and the Atheros driver.  It's been a problem for almost a year.  The post suggested changing the ethernet MTU from automatic to 9000.  That seems to be working right now.

---

