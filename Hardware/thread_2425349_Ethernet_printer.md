---
title: "Ethernet printer"
date: 2019-08-24
forum: Hardware
---

### Post by allelopath on 2019-08-24
I want to get a printer with an ethernet connection to print from Ubuntu, OS X, and Win 7 & 10.
I want to confirm ... since it is ethernet, I don't need to be concerned about Linux driver compatibility, or do I?
---
Ubuntu 18.04.3 LTS

---

### Post by brian_p on 2019-08-24
> **allelopath said:**
> I want to get a printer with an ethernet connection to print from Ubuntu, OS X, and Win 7 & 10.
I want to confirm ... since it is ethernet, I don't need to be concerned about Linux driver compatibility, or do I?
---
Ubuntu 18.04.3 LTS

Any printer you purchase today will operate on the network with Ubuntu 18.04.3 LTS without any problem. See

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

I don't know about printing from OS X, Win 7 or Win 10.

---

### Post by The Cog on 2019-08-24
I was concerned about compatibility when I bought my last printer. I bought an HP Envy 5030, cheap enough to not mind giving it away if it didn't work. Well, it did work, and without my having to do anything (other than enter the WiFi password on the printer panel - it's not near an Ethernet outlet). When I opened the Printers dialog in Ubuntu, the printer was there waiting to be selected as the default printer. I believe the whole Envy range uses the same software, so I would go for a higher spec version next time, but that base model is pretty good. I'm happy with it.

---

### Post by brian_p on 2019-08-24
> **The Cog said:**
> I was concerned about compatibility when I bought my last printer. I bought an HP Envy 5030, cheap enough to not mind giving it away if it didn't work. Well, it did work, and without my having to do anything (other than enter the WiFi password on the printer panel - it's not near an Ethernet outlet). When I opened the Printers dialog in Ubuntu, the printer was there waiting to be selected as the default printer. I believe the whole Envy range uses the same software, so I would go for a higher spec version next time, but that base model is pretty good. I'm happy with it.

I have an Envy 4500 and have no software to use other than CUPS and cups filters. Drivers for printing? Forget about them. The whole of the HP modern printer range does not need them either. It is taking users a long time to cotton on to viewing vendor printer drivers as no longer compulsory on the printing system.

---

### Post by ajgreeny on 2019-08-24
If you want to use a GUI for any printer management activities that are needed install hplip-gui; it gives you a great printer configuration GUI.

It is not absolutely necessary as the CUPS webmin [http://localhost:631/](http://localhost:631/) can do similarly, but it's an excellent GUI application.

---

### Post by allelopath on 2019-08-25
Thanks for the replies, very helpful.
What is it that makes an HP "envy" printer an "envy" printer, as opposed to say an HP OfficeJet or LaserJet?

Would this [HP OfficeJet Pro 9025]("https://www.amazon.com/HP-OfficeJet-9025-Solutions-Productivity/dp/B07N1DH6MC/ref=sr_1_2?keywords=hp+%22envy%22+laser+printer+ethernet&qid=1566738667&s=gateway&sr=8-2")  be compatible with Ubuntu as well?

---

### Post by brian_p on 2019-08-25
> **allelopath said:**
> 
Would this [HP OfficeJet Pro 9025]("https://www.amazon.com/HP-OfficeJet-9025-Solutions-Productivity/dp/B07N1DH6MC/ref=sr_1_2?keywords=hp+%22envy%22+laser+printer+ethernet&qid=1566738667&s=gateway&sr=8-2")  be compatible with Ubuntu as well?

Check for an AirPrint service on it using

[https://wiki.debian.org/QuickPrintQueuesCUPS](https://wiki.debian.org/QuickPrintQueuesCUPS)

---

### Post by allelopath on 2019-08-25
Ah, so [on the HP site]("https://store.hp.com/us/en/pdp/hp-officejet-pro-9025-all-in-one-printer") it says:
Mobile Printing Capability: HP Smart; Apple AirPrint&#8482;; Wi-Fi® Direct Printing; Mopria&#8482; Certified

So this is ethernet, not wire, but through a wireless network, yes?

---

### Post by SeijiSensei on 2019-08-25
I'm very happy with my Brother HL-3170CDW which I have hard-wired into my router with an Ethernet cable. Since all my devices are on the same subnet, I can print wirelessly to it as well. (That particular model has been replaced with the HL-L3230CDW. Costs $229 at [Amazon]("https://www.amazon.com/Brother-HL-L3230CDW-Providing-Wireless-Replenishment/dp/B07FMYYXZD/").) I'm using third-party cartridges with it without a hitch.

The most important thing is to give the printer a static IP address like you would any server.

---

### Post by brian_p on 2019-08-25
> **allelopath said:**
> Ah, so [on the HP site]("https://store.hp.com/us/en/pdp/hp-officejet-pro-9025-all-in-one-printer") it says:
Mobile Printing Capability: HP Smart; Apple AirPrint™; Wi-Fi® Direct Printing; Mopria™ Certified

So this is ethernet, not wire, but through a wireless network, yes?

Ethernet or wireless would do. Actually, USB is also supported via ippusbxd.

---

### Post by allelopath on 2019-09-01
I bought a the CDW you specified. Just set it up. Could not have been easier. Thanks!

---

### Post by brian_p on 2019-09-01
> **allelopath said:**
> I bought a the CDW you specified. Just set it up. Could not have been easier. Thanks!

That is what we want to hear. Installing a modern printer on a recent Ubuntu really is snap.

Thanks for the feedback and - Happy Printing!

---

### Post by Skaperen on 2019-09-01
112 trees are angry with CUPS.

---

