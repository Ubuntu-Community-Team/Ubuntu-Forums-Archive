---
title: "Linksys WUSB11 Version 2.8 Lucid"
date: 2010-05-14
forum: Hardware
---

### Post by opensourceguy on 2010-05-14
Hi everyone, I just upgraded my desktop PC from 9.10 to 10.04.  I use a Linksys WUSB11 Version 2.8 to connect to my home Wi-Fi network but when I upgraded to Lucid Lynx it stopped seeing my USB Linksys as a network device.  I had to blacklist a driver to get it working in Karmic (which I tried but does not work in Lucid) as shown at 
[http://swiss.ubuntuforums.org/showthread.php?p=8051588](http://swiss.ubuntuforums.org/showthread.php?p=8051588)
 I know it sees it in Lucid because it was listed as a USB device to the computer. I've been down the ndiswrapper route, tried the Atmel USB drivers at BerliOS (Fatal error when compiling) and also the atmelwlandriver over at SourceForge (Fatal error but may need to recompile kernel but do not at the moment know how to do that, as I am still a relative newbie)  Any help will be greatly appreciated.  Thanks!

-- OpenSourceGuy

---

### Post by pdc on 2010-05-15
I think if you google on this topic, and look on the wireless forum, where advice on wireless devices can be sought, there have been problems; many would suggest that before moving ahead to "*upgrade*" one should check with a liveCD install that ........ all works ....... that one would wish to work

---

### Post by opensourceguy on 2010-05-15
You know in hindsight that sounds like a much better idea to check if it works. 8-) I'm currently building the kernel sources for the install of another driver, but if it doesn't work I'm probably either going back to Karmic or finding a supported PCI Wi-Fi card.  I'll do a search on the wireless forums too.  Thanks for your help!

---

### Post by opensourceguy on 2010-05-15
Just solved it. I also put up a post at [http://ubuntuforums.org/showthread.php?p=9306475](http://ubuntuforums.org/showthread.php?p=9306475)
Thanks!

---

