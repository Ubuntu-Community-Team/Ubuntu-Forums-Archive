---
title: "Ubuntu 10.10 on Compaq Mini CQ10-405DX"
date: 2010-12-01
forum: Hardware
---

### Post by smoovew on 2010-12-01
Off the bat, Ubuntu Netbook installed great on this new netbook (one of the Best Buy doorbusters from Black Friday).

There is one issue I have come across. When shutting down, the laptop locks up the desktop and does not power off or reboot. At this point the netbook needs to be cycled by holding down the power for 10 seconds. When it comes back up, it is as if nothing was wrong, either in Ubuntu or Windows (dual booted Win 7 64bit, works nicely).

I don't have a lot of free time to tear into the machine. Are there any known issues with Ubuntu shutting down (or not shutting down, as the case may be)on other netbooks?

---

### Post by WrightPC on 2010-12-04
I found my answer [here]("https://answers.launchpad.net/ubuntu/+question/132350").
Add "blacklist rt2800pci" to "/etc/modprobe.d/blacklist-wlan.conf" with the following command:
```
sudo echo "blacklist rt2800pci" >> /etc/modprobe.d/blacklist-wlan.conf
```then reboot. 

Suspend to Ram works reliably.
Hibernate to disk works reliably.
Random boot failures have disappeared.

All is well.

---

