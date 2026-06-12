---
title: "WiFi: USR 5420 and Latest Kernel Update"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by gorkon on 2005-08-20
I applied the latest Kernel update from Ubuntu and rebooted a while later then bam...no network......hmm....let me investigate....

I use ndiswrapper with USR's windows driver(to get WPA suport).  Tripped through dmesg and found BEFORE ndiswrapper tries to load, it detects as a acx100 chipset.  I dropped acx_pci into the /etc/hotplug/blacklist and bingo....ndiswrapper loades and I finally get a IP over my WPA protected network.  Just thought I would save someone else about 3-4 hours of headbanging! ](*,)    The previous kernel, before loading the Kernel update ubuntu added did not have this issue.  I can only assume the acx wireless module was one that they added.  This may be common Linux guru knowledge, but as Ubuntu is a desktop oriented, alot of other users may find this very useful.

---

### Post by tymek666 on 2005-08-21
I think acx-100 module comes with deflaut kernel too, that's why ubuntu works out of the box with amny wifi cards.

---

### Post by gorkon on 2005-08-23
Strange.  For some odd reason the old kernel worked fine with ndiswrapper configged.  Oh well.  Just added to blacklist and it's been good for 2-3 days now.  I was only able to get this specific card to work with the ndiswrapper (with WPA..worked fine in WEP mode with the acx driver).  Why this card?  Well, Wallyworld had it on clearance for 20 bucks and I figured what the heck!  For 20 bucks, it was a steal of a deal.

---

