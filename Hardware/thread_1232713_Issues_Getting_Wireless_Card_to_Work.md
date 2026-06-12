---
title: "Issues Getting Wireless Card to Work"
date: 2009-08-05
forum: Hardware
---

### Post by aeproberts on 2009-08-05
I have searched high and low on the forums and have yet to find the information I need. 

I have an old Dell 600m with an intel a/b/g wireless card that I believe uses the Broadcom chipset. I have found lots of instructions explaining how to get the drivers to work with that card (though it seems kinda complicated).

Unfortunately, the card will not show up at all on my laptop. All my other cards show up, including my Broadcom wired gigabit card. When I type 'lspci' (I think that is the command) it showed up all kinds of other cards, but no wireless card. When I look under the network settings I see my wired card but no wireless card. I know the wireless card is in there, and it was working fine until I formatted my drive and installed Ubuntu. 

It is frustrating because everything else is working fine, and I am loving Ubuntu so far, but if I can't get wireless internet then the laptop is kinda useless. 

Any help for a complete Linux noob would be appreciated.

---

### Post by aeproberts on 2009-08-05
I have found an unknown device called pan0, but can not seem to figure out IF that is the wireless card and/or how to help Ubuntu recognize it  if it is.

---

### Post by IQRules on 2009-08-05
Do a google search on "lspci" to identify your wireless device.
Then take a look at modprobe command to load the proper driver.

Do you know what is a XTERM command windows?
From that, run this 

$ sudo lspci -vv | grep -i net


Here is the example from my Sony laptop.

~$ sudo lspci -vv | grep -i net
02:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)

---

### Post by aeproberts on 2009-08-06
Thanks.... all i get when running that command is 

0:2:00.0 Ethernet Controller: Broadcom Corporation Netextreme BCM5702 Gigabit Ethernet (rev02)

There is no entry for my wireless card. I realize that you migh be thinking, "he doesn;t have a wireless card", but I swear to you there is on in the computer and it was working in windows 30 minutes prior to formatting and installing UBUNTU. 

Anything else I can do to get it to show up?

---

### Post by Slasher The Great! on 2009-08-06
this is what i use
NetworkManager Applet 0.7.0.100

---

### Post by aeproberts on 2009-08-06
> **Slasher The Great! said:**
> this is what i use
NetworkManager Applet 0.7.0.100

For a noob....how do I do that and/or where do I find that?

---

### Post by Haleysddad2004 on 2011-08-28
I am having the same problem. I have loaded Ubuntu on my Inspiron 600m and can't get the wireless card (that ironically worked well with windows) to work. Were you ever able to get yours running?
Steve

---

