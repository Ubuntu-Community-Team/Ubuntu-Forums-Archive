---
title: "How do you configure wifi on a laptop?"
date: 2009-04-20
forum: Hardware
---

### Post by vistadude on 2009-04-20
I got a friend that I got using Linux, and I have never used wifi in ubuntu, so Im not sure how u configure it. Anyways, he has a linksys router, it's set up as a closed network, and his laptop is a HP. How do u configure wifi for ubuntu 8.10?

---

### Post by HousieMousie2 on 2009-04-20
Might take a look at this:

[Comprehensive ndiswrapper troubleshooting guide]("http://ubuntuforums.org/showthread.php?t=885847")

... er, it uses Windows drivers to make the wireless card work in Linux.  With so many headaches trying to find the details of the wireless device, many people opt for this solution.  Some manufacturers are known to swap out chips without bothering to change the 'model' information, so two "identical" devices can require two very different drivers.

More information about the device will be helpful for determining if it can be made to work using Linux drivers.

From the link above, check out the part about the "lspci -nn" command it should tell you most of what you need to know to find the Linux driver... starting with if his machine sees the device.

Good luck! :D

---

