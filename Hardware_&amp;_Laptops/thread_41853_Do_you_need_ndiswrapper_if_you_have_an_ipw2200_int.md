---
title: "Do you need ndiswrapper if you have an ipw2200 interface?"
date: 2005-06-15
forum: Hardware &amp; Laptops
---

### Post by dpod on 2005-06-15
Hi all, I have a question. Since there is so much outdated information about wireless in the ubuntu domain, I thought I'd ask the question directly.

I have a brandnew reinstallation of ubuntu on an Acer Aspire 1410. The wireless interface is a Linksys [Airconn] INPROCOMM IPN 2220. I've followed the instructions in the howto for installing WPA supplicant, etc.

In my previous installation of Ubuntu on this computer, I used ndiswrapper to drive the card, and it worked fine. But if I have an uptodate version of the ipw2200 driver running, I'm guessing I might not need to do that this time (I certainly hope so, as I've converted the computer to Ubuntu alone, and hence don't have a windows driver to aim at)

Two questions:
1) is this right that I don't need to use ndiswrapper+windows driver is I have ipw2200 installed correctly?

2) If so, why can't I find my wireless interface with iwconfig? I've added it to my /etc/network/interfaces directory

---

### Post by luca_linux on 2005-06-15
Yeah, you're right. 
You don't need anything else with ipw2200 driver. The latest version works just fine.

---

