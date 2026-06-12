---
title: "Atheros 5006EG wireless card - old problem, new slant! Ndiswrapper problems"
date: 2008-12-20
forum: Hardware
---

### Post by greg.harvey on 2008-12-20
Hi all,

My girlfriend's Gutsy-running Acer Aspire 4315 was running wi-fi fine with an Atheros 5006EG mini PCI card. I remember I had to do some faffing to get started, but after that no real problems. However a recent update (AFAIK, it just happened and my girlfriend doesn't even know how to sudo, so she can't have broken anything!) has knackered wireless networking.

Previously I successfully used madwifi by following this:
[http://ubuntuforums.org/showthread.php?t=669267](http://ubuntuforums.org/showthread.php?t=669267)

I confess I haven't tried this again *yet*, but I'm on the edge of giving up and re-following. I'm actually trying ndiswrapper.

I downloaded the driver from Acer themselves for Win XP, extracted it to /opt/acer/atheros and used the ndiswrapper GUI to install the driver. All good, no problem, hardware present = yes...

But an iwconfig reveals no device - just eth0 and loopback. Reboot. Nothing. Try the driver from the card manufacturer, same story. lspci shows the device, driver installs and says the device is present, but it never appears in ifconfig or iwconfig. For the record, I've followed this to the letter, including all the blacklist stuff:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

Any ideas??? It's driving me nuts. =(

Rgds,

---

### Post by greg.harvey on 2008-12-21
Did it with Madwifi again - success! But the driver has moved, for the record:
[http://madwifi.org/ticket/1192](http://madwifi.org/ticket/1192)

---

