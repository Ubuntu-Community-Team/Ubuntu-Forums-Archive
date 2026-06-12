---
title: "HP dv5000 Broadcom card + 9.10 = &quot;disconnected&quot;..."
date: 2009-12-24
forum: Hardware
---

### Post by mahdimc on 2009-12-24
Hello everyone,

I've been using Ubuntu for a while now without issues since 6.04 but only now, in 9.10, does my laptop's wireless card not work...
I click on the wireless/network icon in the tray, near the clock, and it only shows both "Wired" and "Wireless" as "disconnected".  My wireless card used to work in all previous versions -- it's a Broadcom internal card found in the HP DV5000 (I can't remember or find the exact name in Windows).

Also, here's my iwconfig output, if it helps:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

If there's any other information you need, just let me know, I'll be glad to give it to you. :)

EDIT: Also, when I click on the "Hardware" option in System > Administration, it says my system has "no restricted drivers" or something of that sort.  It used to tell me my wireless card driver was restricted and would show it in a list in previous Ubuntu versions.

---

### Post by mahdimc on 2009-12-24
Bump...
...No ideas or solutions, anyone?

---

### Post by Ayuthia on 2009-12-24
If it does not show up in Hardware Drivers, then you might try going into the Terminal or using Synaptic to install b43-fwcutter:
```
sudo apt-get update
sudo apt-get install b43-fwcutter
```
However, you do need a working internet connection to get it to install correctly because it needs to download the firmware to help make the driver work.

---

