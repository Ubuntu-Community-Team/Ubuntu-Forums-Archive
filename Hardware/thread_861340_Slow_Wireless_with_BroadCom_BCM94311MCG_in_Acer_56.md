---
title: "Slow Wireless with BroadCom BCM94311MCG in Acer 5620-4025"
date: 2008-07-16
forum: Hardware
---

### Post by zggame on 2008-07-16
I got this laptop (Pentium 2390, 1G RAM, 120G) this week and put the Ubuntu 8.0.4 into it along with the original Vista. Most things work well.  It pops up the window about the proprietary firmware from Broadcom and I click yes.  The wireless works but quite poorly.  :(  It can only get a very strong signal (a 54M 802.11g router in the room, or right in the classroom with good university wireless) in 1M/s mode.  It takes long time to connect and breaks from time to time.  It works just fine in vista, get good signal in the same situation.  I checked with "iwlist scan", it shows very high noise level.  In the same room, another laptop will report about signal/noise 40dBm/90dBm, this laptop reports something like 40dBm/45dBm.  And it fluctuates, a bit later it shows 40dBm/70 dBm, and goes back a bit later again.  

Any idea about this?  I found some posts about this card.  Should I try it? :confused:

---

### Post by zggame on 2008-07-20
This [pos]("http://ubuntuforums.org/showthread.php?t=766560") helps me out mostly.  It now detects the noise as 96dBm and has speed 54m/s.  It disconnects occasionally but generally works fine.

---

### Post by Dark_Stang on 2008-07-20
Glad you found the solution. You have the same card as I do. The open source drivers are incredibly buggy for our wireless cards at this point so using ndiswrapper is recommended.

---

### Post by zggame on 2008-07-25
Thank you for the information.  Hopefully, they will get it fixed in the near future.

---

### Post by zggame on 2008-08-16
I am using ndiswrapper from this postfor my laptop (Acer 5620-4025, Pentium 2370, 1G RAM, 120G Ubuntu 8.0.4). It works quite irregularly. Sometimes it works just fine. But sometimes it just refuse to connect. Here are a few symptoms. I am using the networkmanager to manage the wireless.

1. It always like to connect to a very week unsecured 802.11b network instead the 802.11g WPA-PSK in my home.

2. It always take long time to connect to my 802.11g wpa network, really long time. A few minutes would be normal. Sometimes it doesn't connect at all. It often doesn't connect when I turned the laptop on, then I have to choose my network by left-click the network icon and choose mine. Then it will connect to the unsecured one, I have to choose mine network again. It sometimes work after a few try. I know the network and key are just fine because another laptop with WinXP works just OK. Similar thing happens when I am in school, it reluctant to connect to the WPA2 network, although the signal is as strong as the unsecured one.

3. Sometimes, the connection breaks off spontaneously.

Most problems seem with the secured network. Here are the logs for network (my wireless device is wlan0)

Aug 14 00:04:19 tigger-laptop NetworkManager: <debug> [1218690259.275608] nm_device_802_11_wireless_get_activation_ap(): Forcing AP '100AcreWoods'
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / 100AcreWoods
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Deactivating device wlan0.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0): cancelling...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) cancellation handler scheduled...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0): waiting for device to cancel activation.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) cancellation handled.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0): cancelled.
Aug 14 00:04:19 tigger-laptop NetworkManager: <WARN> nm_device_802_11_wireless_set_essid(): error setting ESSID to '' for device wlan0: Invalid argument
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Device wlan0 activation scheduled...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) started...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0/wireless): access point '100AcreWoods' is encrypted, but NO valid key exists. New key needed.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) New wireless user key requested for network '100AcreWoods'.
Aug 14 00:04:19 tigger-laptop NetworkManager: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.


BTW:

It always show in the network icon "Waiting for Network Key for the wireless network '100AcreWoods'..."

Another update: I disable the WPA in the router and the laptop connected quickly with ease. So it seems some bad interaction of the WPA. The key I entered in "WPA personal" is correct for sure. Where should I start?


update again: I tried WEP 128 with my router and it works on my laptop as quickly as unsecured network. So maybe just the WPA?

my router is Belkin 802.11b/g F5D7230-4:confused:

---

### Post by Ayuthia on 2008-08-16
You might try this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
It will require you to use the pre-release kernel version.  Broadcom has come out with a linux driver, wl.  It works well with my 4311 rev 01 card.  If you don't want to use the pre-release kernel, you can go to the Broadcom site and download the driver there:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I have not tested it on 2.6.24-19-generic, but I don't think that it should be any different.

Configuring the wl driver will be like ndiswrapper mainly because the ssb driver will cause conflicts with the wl driver if it is loaded before the wl driver.

---

### Post by zggame on 2008-08-19
It seems to have something to do with the keyring.  It looks like the keyring keeps the passphrase from the wireless.  I clear the keyring in the password keyring and it asks for the wpa passphrase and then connects in a moment after I entered it.  But next time, I have to clear it again.

---

### Post by zggame on 2008-08-24
It works for me. Thanks.

> **Ayuthia said:**
> You might try this link:
[http://ubuntuforums.org/showthread.php?t=880218](http://ubuntuforums.org/showthread.php?t=880218)
It will require you to use the pre-release kernel version.  Broadcom has come out with a linux driver, wl.  It works well with my 4311 rev 01 card.  If you don't want to use the pre-release kernel, you can go to the Broadcom site and download the driver there:
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

I have not tested it on 2.6.24-19-generic, but I don't think that it should be any different.

Configuring the wl driver will be like ndiswrapper mainly because the ssb driver will cause conflicts with the wl driver if it is loaded before the wl driver.

---

