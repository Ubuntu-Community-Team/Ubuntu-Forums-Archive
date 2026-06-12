---
title: "Losing connectivity with ath9k on Macbook2,1"
date: 2009-04-11
forum: Hardware
---

### Post by tfc on 2009-04-11
Hello there,

I am using an atheros WLAN-card ( ar5008 ) in a Macbook2,1 and am experiencing connectivity-problems.

The ath9k-module in the (ubuntu8.10) 2.6.27-kernel was able to connect to my network at home, but quality's really poor. Speed was around 1Mbit/s and connectivity was unstable.

Then i compiled the latest kernel from kernel.org (2.6.29.1). The ath9k-module in this kernel's really fast and link-quality is as good as it is in OS X.

But after a random amount of time the devices "pauses" working and then continues. NetworkManager doesn't show any "disconnected"-information and lets all applications think they're still online. I found some output, though....:

/var/log/sysinfo is saying:
```

Apr 10 13:45:19 photon NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 4 
Apr 10 13:45:19 photon NetworkManager: <info>  (wlan0): supplicant connection state change: 4 -> 5 
Apr 10 13:45:20 photon NetworkManager: <debug> [1239363920.985469] periodic_update(): Roamed from BSSID 00:DE:AD:BE:EF:94 (WLANS SSID) to (none) ((none)) 
Apr 10 13:45:23 photon kernel: [  727.793146] wlan0: beacon loss from AP 00:DE:AD:BE:EF:94 - sending probe request
Apr 10 13:45:23 photon kernel: [  727.800796] wlan0: deauthenticated (Reason: 6)

```

I don't know what "reason SIX" means, so i was looking for an answer in the kernel. I found something in include/linux/ieee80211.h :
```
WLAN_REASON_CLASS2_FRAME_FROM_NONAUTH_STA = 6,
```
But i don't understand what this constant's name means.

After reloading the module it sometimes happens that NetworkManager thinks the password is wrong and asks me for a new one....

Using the latest compat-wireless-kerneltree doesn't change anything.

The wireless network is a draft-n one.

Anyone having the same problem and/or a solution?

---

### Post by _oOMOo_ on 2009-04-16
I'm experiencing this in Jaunty using the linux-backports-modules package, which uses the latest(ish) drivers. There's some info on the kernel mailing list about it, unless I've read it all wrong it appears that when network manager scans for networks every 120 seconds, the link is temporarily broken. 

Here's the link to the relevant mail:

[http://lkml.org/lkml/2009/4/6/41]("http://lkml.org/lkml/2009/4/6/41")

In the meantime I'm going to install wicd and see if there's any change.

---

