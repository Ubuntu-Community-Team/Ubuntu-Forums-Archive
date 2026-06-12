---
title: "Persistent Bluetooth disconnection woes"
date: 2014-06-07
forum: Hardware
---

### Post by daniel-clement on 2014-06-07
Hello,

On my wife's Dell XPS 13 laptop, we are still facing Bluetooth disconnections after installing Trusty (the PC came with Precise). The Bluetooth mouse sometimes loses connection, but only when battery-powered. So I'm thinking of a power management issue. 

I have had some ideas since [the beginning of these problems]("http://ubuntuforums.org/showthread.php?t=2216322"); I've thought of possible fixes:
1) disable BT power management, but how should this be done? Somewhere under /sys/class/bluetooth/... there's a "control" file with "auto", which I tried to replace with "on", but the change was rejected (in spite of admin rights);
2) use ndiswrapper to install a Windows driver for the Intel 7260 WiFi+BT card -- but I've never done that, or...
3) install another card. But it's the new NGFF micro format, and the only other one I've found is a Broadcom BCM94352. Not only is it difficult to source, but I'm not sure it would be supported under Ubuntu.

As you can see, I'm well in need of advice. TIA, best regards, Daniel

---

