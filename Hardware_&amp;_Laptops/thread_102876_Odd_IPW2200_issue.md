---
title: "Odd IPW2200 issue"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by Xocet on 2005-12-13
Okay, I've done a cursory check of the existing forum threads and don't see anyone with this issue. Sorry if I am double-posting an existing problem.

I have a Toshiba Satellite M40 that uses a Intel PRO/Wireless 2915 chipset. When I do a default install of Ubuntu 5.10 my card is recognized. I can configure it. It even associates with my AP. My link quality is usually listed as '98', but here's where it gets weird: I invariably get Signal Level: 0, Noise Level: 198 (or some similarly large number). I can't transmit or receive any traffic. I have tried a variety of things to fix this problem. 

I have tried downloading, compiling and running every version of IPW2200 since the 1.0.0 release, along with the appropriate IEEE80211 and firmware versions. The results in every version are exactly the same. I have used dmesg to check that the new versions are being loaded each time, and have confirmed that they are. I also downloaded an rfswitch package to see if a software radio switch was causing my problem, and while I do have one of the support BIOSes, echoing a 1 to the device also had no effect.

I am at a complete loss. I installed an old DWL 650 (Prism II) card I had lying around and disabled all encryption on my access point (a Linksys WRT54GC-J) and was able to connect fine with the old card. I cross-referenced the listed Access Point MAC in iwconfig and they match for both cards.

So, my Intel 2915 can see and associate with my AP, but it can't talk to it. Driver versions appear to have no effect. I have been unable to find threads with anyone else using this laptop model (PSM40C-YP300E) or any other model in the M40 line. 

One oddity: I upgraded to 2.6.12-10-386 once I got the Prism2 card running and after the first reboot (and the first reboot ONLY) my 2915 was able to communicate with my AP. After a reboot, it was back to the old behaviour.

---

### Post by daller on 2005-12-13
Check this out:

[https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM40-JM8?highlight=%28M40%29](https://wiki.ubuntu.com/LaptopTestingTeam/ToshibaSatelliteM40-JM8?highlight=%28M40%29)

...Don't know if it's helpful, but it worth a try!

---

