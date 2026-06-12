---
title: "Cannot detect Wireless Card"
date: 2009-11-09
forum: Hardware
---

### Post by noahgelman on 2009-11-09
I just installed Ubuntu 9.10 (Was running XP, now dual boot) and it was unable to connect to the internet. It's not able to detect my hardware. I've tried the harware detection from the top menu.

I have a **Compaq Evo D510 Small Form Factor** and my wireless card is a **NETGEAR WG311 v2 802.11g Wireless PC Adapter.**

I know my computer isn't exactly new. There a way for me to install the drive or get it to detect or whatever it is I need to do?

I'm still fairly new to Linux, and I dont know how to do some things, so any specific instructions would be greatly appreciated.

---

### Post by Rayve on 2009-11-09
Try here: [https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)  Something there may help. :)

Good luck!

---

### Post by noahgelman on 2009-11-09
I've decided with much more browsing to use ndiswrapper to install the driver. I have .sys, .inf, and .bin files for my card, but I need to install ndiswrapper. I have a fresh install of 9.10 from the live cd and there are no ndiswrapper files in the Synaptic Package Manager so I can't install it through there. There another way to install it without the Synaptic Package Manager and without Internet?

Remember, I'm still pretty new to Linux and it's the first time I'm encountering this problem so basic or simple explanations/instructions are greatly appreciated (especially when it comes to the Terminal code to do certain actions).

---

### Post by Rayve on 2009-11-09
Here is the sourceforge page for ndiswrapper - [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Main_Page)

From there, you can get to the download page through a link at the bottom, and my guess is you can just download the .tar.gz file of the most recent stable version (appears to be 1.9) and then burn it to CD in order to transfer it to your computer that does not have internet. 

Or, you can just connect with a wired connection and then use Synaptic that way - I always prefer to use Synaptic in case of any dependencies; plus, then I know it's going to the proper place.

---

