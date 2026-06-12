---
title: "Atheros AR242x wireless controller and compat-wireless"
date: 2009-08-01
forum: Hardware
---

### Post by Something Else on 2009-08-01
I've been using a budget-line Compaq laptop which has an AR242x wireless controller from Atheros. It was running out of the box when I first put 8.10 on the system, but future kernel upgrades stopped the drivers from working - so I'd just been booting into an old kernel. After upgrading to 9.04, however, it was working out of the box again - until I rebooted, and presto! the wireless card was no longer detected by the system, even though there was supposedly an active proprietary driver.

I went to the compat-wireless site, downloaded and made the package, and after typing "make load," it appeared to work. Here's what I got.
```
ath5k loaded successfully
Module bcm43xx not detected -- this is fine
b43 loaded successfully
b43legacy loaded successfully

```
My networking applet now shows a "wireless networks" tab, but cannot see any networks. Further, I installed the wifi-radar package, to make sure it wasn't somehow a problem with GNOME and not the hardware drivers, and the terminal output says:
```
wlan0     Interface doesn't support scanning : Device or resource busy

```

Does anyone have any idea how I can resolve this issue and get my wireless back up and running? If going back to proprietary drivers will work, I'll do it - but I think that was what was working and stopped for no particular reason.

---

### Post by Something Else on 2009-08-01
iwconfig results:

```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

