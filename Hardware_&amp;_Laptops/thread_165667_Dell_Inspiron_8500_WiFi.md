---
title: "Dell Inspiron 8500 WiFi"
date: 2006-04-24
forum: Hardware &amp; Laptops
---

### Post by chriskilmer on 2006-04-24
I'm new to Ubuntu and I just installed Breezy for the first time on my Dell Inspiron 8500.  I'm trying to configure my WiFi.  The first problem that I've run into is that the Network settings applet (System->Administration->Network) does not even list my WiFi card.  I can only see my onboad nic (eth0) and modem (ppp0) in the list.  I've googled my head out looking for the solution.  One post I found mentioned setting pci=noacpi.  I made the changes in /boot/grub/menu.lst, though I'm not sure I did it correctly.  I've only been using Linux for the past few months (Debian) and Ubuntu for the last few days.  So, any help would be appreciated (hand holding welcome :-) 

Thank

---

### Post by Mr Fat Bat on 2006-05-15
I'm not sure about using Breezy but in Dapper I tried a few things, the first thing i'd recommend to try would be the Network Manager [http://www.ubuntuforums.org/showthread.php?t=144820]("http://www.ubuntuforums.org/showthread.php?t=144820")

Let us know if it works!

---

### Post by slightly72 on 2006-05-15
That Inspiron model uses a Broadcom WiFi chip (even if it's labeled Dell Truemobile) which doesn't have drivers for Linux (the company refuses to release the specs), so you should use ndiswrapper to load them -- that's what I've done on my inspiron 5160, also with a broadcom chip, and it works just fine. See here: [https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto]("https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto") for how to do that.

You can check the compatibility list for ndiswrapper at: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/List")

---

