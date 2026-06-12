---
title: "Blacklist not functioning?"
date: 2008-10-29
forum: General Help
---

### Post by Bob535 on 2008-10-29
Hello,

I have a laptop, an acer aspire one. It has always had issues with wireless and the drivers used have changed a couple of times so we are supposed to blacklist old modules to let the new one work.

I added all three modules that I know about to the blacklist(see below for what I wrote), and then commented out the most recent, the ath5k module using # at the start of the line.

When rebooted, the results of "lsmod | grep ath" showed that the "ath_pci" and "ath_hal" are still loaded in addition to the ath5k. If I uncomment the "ath5k" line, and let it be blacklisted. Upon reboot only the first two show up.

Any ideas why the first two will not go away and let ath5k work?
Am I confused about how the blacklist works?
Am I confused about ath_pci and ath_hal and how they function?

More specific information about the laptop I have and ubuntu can be found at [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne) but unfortunately I could not find anything to help me.

--------------------

I added the following to /etc/modprobe.d/blacklist
blacklist ath_pci
blacklist ath_hal
blacklist ath5k

--------------------

Thanks

---

