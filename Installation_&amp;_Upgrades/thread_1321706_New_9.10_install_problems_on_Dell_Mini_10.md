---
title: "New 9.10 install problems on Dell Mini 10"
date: 2009-11-10
forum: Installation &amp; Upgrades
---

### Post by critmcdonald on 2009-11-10
After having problems upgrading from 9.04 to 9.10, I just did a fresh install of 9.10 Ubuntu Netbook Remix (UNR) and I have the following issues. One is a newb issue I'm just being stupid about, I'm sure. The other is more serious.

* I can't connect to Wireless networks. Or, I should say, Ubuntu is not looking for existing wireless networks that are broadcast. The first thing I did is check my account privledges to make sure I'm allowed to connect to Wireless, and indeed I wasn't, so I corrected. However, still no networks show under the wireless icon at top-right of screen. The list shows only ("Wired Network disconnected" and "VPN Connections"). This remained so even after a restart of the machine.

* The other issue is the screen redraw, which is freaking horrible. When I ran 9.04 I had the same problem, but I found some help by adding Poulsbo graphics drivers. The instructions I have did not work for 9.10, though. Anyone know if a) that would help and b) where to find Karmic-friendly versions of this?

---

### Post by RochJer on 2009-11-10
1. When you logged in or auto login, you should receive the authentication access to type in password to start Network Authenticate to enable wireless networking. Did you come up with this dialog box? 

2. The screen redraw - did you mean that your panel (top taskbar) did not fit correctly on your screen? If so, you are correct, it is possibly your graphic card. Try typing in Synaptic Package to see if your video card is supported in Ubuntu for Poulsbo video card. I have had similar problem with screen not fitted with my NVIDIA GeForce 5200, but it had restricted driver came up telling me to update NVIDIA driver to version 1xx then it worked. See if your video card can update.

---

### Post by witeshark17 on 2009-11-10
> **critmcdonald said:**
> 
* I can't connect to Wireless networks. Or, I should say, Ubuntu is not looking for existing wireless networks that are broadcast. The first thing I did is check my account privledges to make sure I'm allowed to connect to Wireless, and indeed I wasn't, so I corrected. However, still no networks show under the wireless icon at top-right of screen. The list shows only ("Wired Network disconnected" and "VPN Connections"). This remained so even after a restart of the machine. Are you sure a hard circuit switch for the wireless card is on, either on the side of the netbook or one of 
the keys (F2 on my Dell, with a graphic of a radio tower)?

---

### Post by digerati on 2009-11-16
I had the same issue on my Dell Mini 10v after using the wubi installer bundled with the iso.  The solution posted in this forum resolved it.
[http://ubuntuforums.org/showthread.php?p=8253721](http://ubuntuforums.org/showthread.php?p=8253721).

---

### Post by leigh_j_d on 2009-11-30
I had the same problem on a dell mini 9, no wireless networks appearing because there were no proprietary drivers visible for the broadcom.

I managed to get it going by fumbling through.

Managed to update using a netgear wifi key, which worked fine, then searched for proprietary drivers in hardware drivers, activated the broadcom driver which now appears and no problems since.

Thing I don't understand is why it finds the drivers when booting ubuntu from live disk (usb key)  but not after install.

---

