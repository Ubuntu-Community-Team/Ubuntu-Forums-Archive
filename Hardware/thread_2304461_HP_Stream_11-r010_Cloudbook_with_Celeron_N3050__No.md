---
title: "HP Stream 11-r010 Cloudbook with Celeron N3050:  No Wi-Fi (greyed out)"
date: 2015-11-26
forum: Hardware
---

### Post by Jerry_Gorland on 2015-11-26
Hi, Everyone,

I recently bought an HP Stream 11-r010 netbook which comes with the Celeron N3050, Windows 10 and the Realtek RTL8723BE Wi-Fi chip.  I have read various threads about successes with Linux on prior versions of the laptop.  However, I have booted into **live 64-bit **versions of Xubuntu 15.10,  Fedora 23.10, Mint 17.2 (also tried the 32 bit version), but in each case the Wi-Fi network manager GUI shows the items "Wi-Fi Networks" and "disconnected" to be greyed out.  It recognizes no available wireless networks.  For some reason the RTL8723BE just won't fully engage with Linux.

With Min 17.2 live usb:

  nm-tool shows a state = "unavailable" or "disconnected" when I disable/enable Wi-Fi in each case. I think this is normal.  In fact, the dedicated "airplane" button does toggle the setting. The driver is recognized as rtl8723be.  However, the "Capabilities" section is blank (i.e., no capabilities?).

dmesg indicates near the end of the log "IPv6: ADDRCONF (NETDEV_UP): wlan0: link is not ready".

lspci identifies the wi-fi controller as "Network Controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Aadapter"

lsusb identifies it as "Bus 001 Device 005: ID 0bda:b006 Realtek Semiconductor Corp."

ifconfig shows wlan0 to be present.

iwconfig shows wlan0 with Tx-power = 20dBm, Power Management = off.

sudo lshw -C network describes the RTL8723BE with "configuration: broadcast=yes driver=rtl8723be driverversion=3.16.0.38-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn"

modinfo rtl8723be returns:
- filename = /lib/modules/3.16.0.38-generic/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
- firmware = rtlwifi/rtl8723befw.bin

Does anyone have a similar, recent experience like me?   Perhaps it's a "live linux" problem/limitation?

Cheers and thanks for your help!

---

### Post by matthew82 on 2015-11-27
By chance, are you using live persistence?

---

### Post by Jerry_Gorland on 2015-11-27
No, it is not persistent.  However, upon further digging I think that the fact that lshw returns "firmware=N/A" is not a good thing.  And yet I see a file under:  /lib/firmware/rtlwifi/rtl8723befw.bin.  I know that the wireless card used in the laptop supports Wi-Fi and Bluetooth.

---

### Post by Jerry_Gorland on 2015-11-30
Quick update:  When I booted from the live Mint 17.2 stick, and walked past my router (within 10 feet), my laptop saw it.  It even connected!  So this problem is the "RTL8723BE reduced range" problem that has been talked about.  I purchased a D-Link DUB-E100 USB to ethernet converter (and it works great) so I can get e-net access to debug further.  I've continued this with another gentlemen who is having issues with the same chip at his thread:  [http://ubuntuforums.org/showthread.php?t=2304607&page=2](http://ubuntuforums.org/showthread.php?t=2304607&page=2).

---

### Post by Jerry_Gorland on 2015-12-06
Just to update this in case some other lost soul is trying to figure out what *might* be going on with their barely-functioning RTL8723BE:  Please see thread [http://ubuntuforums.org/showthread.php?t=2304607&page=2&p=13402744#post13402744](http://ubuntuforums.org/showthread.php?t=2304607&page=2&p=13402744#post13402744) where I found that moving the single antenna cable to the other connector of the Wi-Fi adapter solved the problem!

---

