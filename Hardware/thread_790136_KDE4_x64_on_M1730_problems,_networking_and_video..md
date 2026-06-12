---
title: "KDE4 x64 on M1730 problems, networking and video."
date: 2008-05-11
forum: Hardware
---

### Post by VinylPusher on 2008-05-11
Installed Kubuntu 8.04 + KDE4 x64 on my Dell M1730 yesterday and ran into a few problems.

Firstly, the restricted Nvidia driver was enabled but not in use. I could not see how to get it working (and I've done this peviously with 7.10 Ubuntu successfully). Enabling the advanced desktop effects resulted in an unusable display.

Secondly, when I entered the settings for the wireless network for the first time (manual SSID entry, WPA2 with AES), the network manager crashed.

When I retried the procedure, it succeeded but the wireless network would not initiate (and the wireless LED indicator on the laptop never switched on).

I then tried to connect via wired networking. It took a long time (>10 sec) to pick up an IP address and then traffic was not getting through. 'ifconfig' revealed such wonders as "received: 8, errors: 6". Network manager thought I had a 10Mb connection (it should be 100Mb). No amount of resetting the adapter resulted in a successful connection. I could not even ping my router.

I will try installing vanilla Ubuntu 8.04 x64 at some later point but ISTR that I had similar issues with Kubuntu previously (5-6 months ago).

---

