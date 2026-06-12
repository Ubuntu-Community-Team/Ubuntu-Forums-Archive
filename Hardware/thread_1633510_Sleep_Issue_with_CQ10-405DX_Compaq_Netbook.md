---
title: "Sleep Issue with CQ10-405DX Compaq Netbook"
date: 2010-11-29
forum: Hardware
---

### Post by Panoramicpants on 2010-11-29
So I recently purchased the Best Buy Black Friday netbook, the Compaq CQ10-405DX and successfully installed Ubuntu Netbook Edition 10.10.  Things are going great with the exception of one thing - I cannot get the netbook to successfully go to sleep.  When I close the netbook or tell it to hibernate, the screen goes blank, but remains on, as does the rest of the machine.  I cannot get it to wake from this state and must hard reboot.  This isn't ideal, as I'd like to be able to close and open the machine at will.  Any suggestions on a fix for this?

Thanks!

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

