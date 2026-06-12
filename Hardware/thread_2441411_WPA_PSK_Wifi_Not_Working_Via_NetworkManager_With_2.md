---
title: "WPA PSK Wifi Not Working Via NetworkManager With 2015 MacBook Pro on 20.04"
date: 2020-04-23
forum: Hardware
---

### Post by agreenbhm on 2020-04-23
I recently installed the latest nightly of 20.04 on my mid-2015 MacBook Pro 15" (11,5 model).  The WLAN card is the BCM43602, which has the id 14E4:0152.  I've been trying many different things to get it to connect to a WPA2 wifi network using the gui (NetworkManager), but so far have not had any success.  I can see the networks listed, but when I try to connect and enter my PSK, it eventually errors out and say I need to re-enter the PSK.

The strange thing though is that I can connect using wpa_supplicant.  I can also connect using NetworkManager to open networks, just not ones using WPA-PSK (and not sure about WEP or WPA-Enterprise).  I've used wpa_supplicant on the cli to connect manually to my network at home, and I configured netplan to use networkd as the renderer to connect to the network automatically.  These both work just fine.

Anything obvious I should be looking at?  The NetworkManager logs are unhelpful, as all it says is associating -> disconnected, repeatedly.  I can post them if needed.  dmesg mentions issues with loading firmware and that channels might be limited, however that seems like a false alert given that I can connect without issue using wpa_supplicant.

Thank you!

---

### Post by CelticWarrior on 2020-04-23
Check this first: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

