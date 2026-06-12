---
title: "Intersil Prism wireless not working under Lucid"
date: 2010-06-18
forum: Hardware
---

### Post by huzzam on 2010-06-18
Hi--

I have an IBM Thinkpad T30 with an internal (PCI) Intersil Prism 2.5 Wavelan wireless card. It worked sporadically under Karmic, but I can't get it going at all in Lucid. Details:

* by default, Lucid loads the "orinoco_pci" driver, which doesn't allow for scanning for networks at all (i.e. none of the nearby networks are listed when I click on the Network Manager applet), nor does it connect to a manually-entered network.

* [_here_]("https://help.ubuntu.com/community/WifiDocs/Device/IntersilPrism25Wavelan") in the Ubuntu help pages (which seems targeted towards Dapper/Edgy), I found recommendations to blacklist these modules: orinoco_pci, orinoco, prism2_pci, & hermes. Doing so prevents Ubuntu from booting; even before the splash screen, the disk stops spinning, I get an error about CPU#0 being frozen for 61 seconds, and it never recovers.

* [_here_]("https://help.ubuntu.com/community/WifiDocs/Device/Proxim%20RangeLAN-DS") on the Ubuntu help pages, I found a recommendation to blacklist hostap_cs, and add orinoco_cs to /etc/modules. The system boots, and even allows the card to scan for & find networks, but it won't connect. Additionally, the "events/0" process starts eating my cpu, with total system pauses every few seconds.

Does anyone have ideas? My girlfriend needs her computer back!

Thanks
~peter in oakland

---

### Post by huzzam on 2010-06-18
[moving to "networking & wireless" forum, sorry]

---

