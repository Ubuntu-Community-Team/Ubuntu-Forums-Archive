---
title: "Broadcomm BCM4306 (v02) wireless card not enabled on Dell Latitude X300"
date: 2009-07-13
forum: Hardware
---

### Post by LLudovic on 2009-07-13
Hi all,


 I'm a Linux newbie and have installed Ubuntu 9.4 (Jauty Jackalope, where do they find those names?) and find it much better than what people said... except for the Wifi driver of my old Dell Latitude X300 with a Broadcom BCM4306 (v2) mini-PCI card.
 I've followed the steps in this post
[https://answers.launchpad.net/ubuntu/+question/67953](https://answers.launchpad.net/ubuntu/+question/67953)
and tried to install the drivers using the bcm43xx-fwcutter as depicted on the blog linked from this page:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom#miniPCI)
and
[http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html](http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html)
[URL="http://davidwatson.org/2007/05/broadcom-4306-on-feisty-fawn.html"]
[/URL]
 What seems to happen is that the PCI Wireless adapter is not enabled (yes, I've tried Fn+F2 and looked for a hardware switch), as the command 'sudo lshw -C network shows:
- my Broadcomm adapter is found as 'network:0' under the logical name 'wlan0'
- when I enter the command 'lshw -C network', it says '*-network:0 DISABLED'
- when I insert a PCMCIA WiFi card (unfortunately it's one of the very first ones and doesn't seem to support WEP encryption), I can "see" the WiFi networks in the neighbourhood but when it's not present the 'Wireless Networks' option in the networking tray icon is greyed out.
 That's why the only think I can work out as a cause is that there's a software switch for wireless that's off, because Ubuntu recognises the card but can't use it.
 Thought anyone?

---

