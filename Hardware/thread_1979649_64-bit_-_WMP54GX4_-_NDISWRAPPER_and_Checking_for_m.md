---
title: "64-bit - WMP54GX4 - NDISWRAPPER and Checking for multiple drivers"
date: 2012-05-13
forum: Hardware
---

### Post by bunkster on 2012-05-13
Hi,

This is my first post. Thanks to all those who have kept me from posting in the past by providing answers for others that also answered my questions too.

I've been looking around for a few hours on this question and I figure I'll give this a go...

My problem is with getting a PCI linksys WMP54GX4 to work on 12.04 64 bit.

I've followed pretty much the same steps from:
[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)
skipping the ndiswrapper removal steps and substituting the driver I have for my device.

I noticed that bcm43xx is already blacklisted from the start on 12.04. When I run lspci -nn, I see:
01:07.0 Ethernet controller: Airgo Networks Inc AGN300 802.11 a/b/g True MIMO Wireless Card (rev 01)

Once I have ndiswrapper install the driver, I have the following results for ndiswrapper -l:
tmimo3p : driver installed
    device (17CB:0002) present

The problem is that in network-admin, the device does not show in the list. I see my other two ethernet devices, just not the wireless one. If I plugin a usb wifi dongle, it loads right up. I am able to configure my SID in network admin but the WMP54GX4 just isn't showing up.

I believe there may be some incompatible module loaded for my device which I need to blacklist. How would I determine if this is the case? Or is it possible that the Airgo Networks Inc information shown from lspci -nn is incorrect?

Thanks in advance

---

### Post by bunkster on 2012-05-15
[http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper)

If I had changed my strategy for researching this problem to just browsing the forums, I think I would have found the answer in the link above.

It looks to me that I was attempting to use a 32 bit driver with my 64 bit kernel. Unfortunately, there is only one windows driver version offered for this device from the vendors website. I'll still follow the rest of the directions in the link above just to make sure that is the problem. Thanks for the post in the link above. I'm sorry I didn't see that sooner.

---

