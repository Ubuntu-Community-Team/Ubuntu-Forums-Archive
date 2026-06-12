---
title: "Broken off Wireless for (BCM94311MCG)"
date: 2008-08-14
forum: Hardware
---

### Post by zggame on 2008-08-14
I am using [ndiswrapper from this post]("http://ubuntuforums.org/showthread.php?t=766560")for my laptop (Acer 5620-4025, Pentium 2370, 1G RAM, 120G Ubuntu 8.0.4).  It works quite irregularly.  Sometimes it works just fine. But sometimes it just refuse to connect. Here are a few symptoms. I am using the networkmanager to manage the wireless.  

1.  It always like to connect to a very week unsecured 802.11b network instead the 802.11g WPA-PSK in my home.  

2.  It always take long time to connect to my 802.11g wpa network, really long time.  A few minutes would be normal.  Sometimes it doesn't connect at all.  It often doesn't connect when I turned the laptop on, then I have to choose my network by left-click the network icon and choose mine. Then it will connect to the unsecured one, I have to choose mine network again. It sometimes work after a few try.  I know the network and key are just fine because another laptop with WinXP works just OK.   Similar thing happens when I am in school, it reluctant to connect to the WPA2 network, although the signal is as strong as the unsecured one.  

3.  Sometimes, the connection breaks off spontaneously.  

Most problems seem with the secured network.  Here are the logs for network (my wireless device is wlan0)

Aug 14 00:04:19 tigger-laptop NetworkManager: <debug> [1218690259.275608] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '100AcreWoods' 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / 100AcreWoods 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Deactivating device wlan0. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0): cancelling... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) cancellation handler scheduled... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0): waiting for device to cancel activation. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) cancellation handled. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0): cancelled. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <WARN>  nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) started... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point '100AcreWoods' is encrypted, but NO valid key exists.  New key needed. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network '100AcreWoods'. 
Aug 14 00:04:19 tigger-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.


BTW:

It always show in the network icon "Waiting for Network Key for the wireless network '100AcreWoods'..."

---

### Post by zggame on 2008-08-14
Another update:  I disable the WPA in the router and the laptop connected quickly with ease.  So it seems some bad interaction of the WPA.  The key I entered in "WPA personal" is correct for sure.   Where should I start?


update again:  I tried WEP 128 with my router and it works on my laptop as quickly as unsecured network.  So maybe just the WPA?  

my router is Belkin 802.11b/g F5D7230-4

---

### Post by zggame on 2008-08-24
I uninstalled ndiswrapper and used the new broadcom driver in the pre-release linux 2.6.24-21. Check[ here]("http://ubuntuforums.org/showthread.php?t=880218").  It works just fine since.

---

