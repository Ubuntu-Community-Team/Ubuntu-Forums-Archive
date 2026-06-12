---
title: "How do I install a display Driver on version 9.10"
date: 2010-03-27
forum: Hardware
---

### Post by luisfm on 2010-03-27
I upgraded to version 9.10 from 8.10. With 8.10 everything was working fine. Here I had some mishaps with the wireless network but Chili555 was extremely helpful. Now onto my next problem. I can see almost everything on the screen, but when the computer comes from sleep, the initial display is all garbled. Also, the message that you get when connecting to a network is just a black rectangle. The Cosmos screen saver (my favourite) is also all garbled. I looked at the file xorg.conf and it does not list  a display driver. My display is an sxga (1400x1050) TFT display with a 4x AGP enables ATI Mobility Radeon 7500 Graphics chip. What should I do?

---

### Post by Mark Phelps on 2010-03-30
Your problem is that 8.10 was the last Ubuntu release that had a working ATI driver for your card.  ATI dropped Linux support for your card early last year, so in every Ubuntu release since then, the default open source drivers are the only drivers that will work.

If you are currently getting a graphical desktop, you have the drivers installed and there's nothing you can do.

If you're not getting a graphical desktop, follow the instructions in the link below for removing the ATI drivers, and reboot -- without creating an Xorg.conf file:

[https://help.ubuntu.com/community/RadeonDriver]("https://help.ubuntu.com/community/RadeonDriver")

---

### Post by luisfm on 2010-04-04
I guess I'll have to live with what I have. For the most part I can see everything. Only hings like the Cosmo Screen saver, and also when the computer is coming out of hibernation. Such is life. Thanks for the answer.

---

