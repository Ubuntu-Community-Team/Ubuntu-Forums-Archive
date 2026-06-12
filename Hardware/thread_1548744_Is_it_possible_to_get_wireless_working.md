---
title: "Is it possible to get wireless working?"
date: 2010-08-08
forum: Hardware
---

### Post by RandyJCB on 2010-08-08
Hey all, so my wireless was working on Windows and now it needs drivers with Ubuntu. The problem is, I don't know which driver, where to get it, or how to apply it. There is no other way to get internet to the computer in question, and this is the information I know so far. It is an Acer Aspire 3680, it says ZR1 on the back. The wired LAN port is broken physically. It is running 10.04 LTS. I don't know the next step, could someone help me out?

---

### Post by jml on 2010-08-08
According to this web site:

[http://www.lecio.us/acer-aspire-drivers/acer-invilink%E2%84%A2-nplify%E2%84%A2-80211bgdraft-n-wlan-driver.html](http://www.lecio.us/acer-aspire-drivers/acer-invilink%E2%84%A2-nplify%E2%84%A2-80211bgdraft-n-wlan-driver.html)

your Acer uses an Invilink 802.11b/g wireless card.  This is based on the Atheros chip set.

If you type lspci from within a terminal,  (You bring up a terminal from the menu bar.  Applications-->Accessories-->Terminal,)  you will see a text output.  Scroll down to the bottom and look for a reference to network controller.  There should be one for the ethernet card and one for the wireless card.  The wireless entry will identify the card.  Then if the Ubuntu disk does not have the driver available, you may have to find and download the driver within Windows before you can install it.  Good luck.

Joe

---

### Post by tlcstat on 2011-03-06
Greetings,
My atheros wifi works automatically on any Ubuntu install. So for a solution you need to know what chip you are using. You can do a lspci from the terminal and look down the list for your wifi chip and post the information. What I usually do is to go to the manufactures site and download the wifi drivers for that system. The chipset will be listed in the driver .inf file. That will positively identify the chip. Without that info a solution is going to be hit and miss.
tlcstat

---

