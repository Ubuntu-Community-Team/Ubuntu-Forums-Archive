---
title: "PCMIA card slot has no power"
date: 2007-02-20
forum: Hardware &amp; Laptops
---

### Post by The_k3rnel on 2007-02-20
Hi all,

I got edgy 6.10 a few days ago after deciding to leave Fedora. It looks lovely and all works well with my Dell 5150 laptop, except of course the wireless networking!

I have searched the forums and read everything I could find on this subject, but alas no answers - hence this post.

I have a Belkin F5D7010 PCMIA card. I am unsure of the chipset but I think it's a Broadcom.

I am trying to use ndiswrapper to get the card working. I am using the bcmwl5a driver. I got the card working with ndiswrapper on fedora so I know it can work.

After a few hours of bashing around with ndiswrapper, lspci and lshw I  convinced myself that I had the right drivers and the card was being detected by the system (eg it appeared under the network connections gui in the main menu). I then noticed this message from dmesg (when I plug the card in for the first time):

[17179688.116000] cs: pcmcia_socket0: unable to apply power.

I am now thinking the card won't work because there is no power to it! Anyone know how to solve this little prob?

Many thanks,
Richard

---

