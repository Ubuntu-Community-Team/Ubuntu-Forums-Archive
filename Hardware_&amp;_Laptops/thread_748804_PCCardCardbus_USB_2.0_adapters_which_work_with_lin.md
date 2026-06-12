---
title: "PCCard/Cardbus USB 2.0 adapters which work with linux/ubuntu"
date: 2008-04-07
forum: Hardware &amp; Laptops
---

### Post by bradtem on 2008-04-07
I have an older thinkpad, and it would be a fine linux server except it doesn't have USB 2.0 high speed.   So I thought the simple plan would be to get a PCMCIA/PCCard/Cardbus with USB 2.0.

However, the first one I bought, a cheap one on eBay works with WinXP but fails to work in gutsy, though it shows up in lspcmcia.

So, I thought a thread here would be useful.   Which models of USB 2.0 cards for laptops have people found to work.    Which have failed?

The one I got has no brand on it, a different ad declares it has the "NEC USB2.0 High-Speed Chip" and it looks like this with a purple triangle on black background:

[http://cgi.ebay.com/USB-2-0-4-Port-PCMCIA-Cardbus-PS-Cable-NEC-Chip_W0QQitemZ270226537773QQihZ017QQcategoryZ42323QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.com/USB-2-0-4-Port-PCMCIA-Cardbus-PS-Cable-NEC-Chip_W0QQitemZ270226537773QQihZ017QQcategoryZ42323QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

So what cards work?  The D-link? The Adaptec?  Thanks.

---

### Post by iamclueless on 2008-04-08
bump

I am interested in the exact same thing

---

### Post by bradtem on 2008-07-01
Hmm.  No info.  I picked up another card, but it turned out to be the NEC chipset agan, so no joy.

These cards, while they work in Windows, seem almost invisible under linux.  They don't show up in lspci -v.   "pccardctl status" does say "3.3v 16-bit pc card" but that's the only indication the card is even in the machine.

So what cards work?  People wanting to take old laptops and make them useful again as linux servers want to know!

---

### Post by bradtem on 2008-07-04
Ok, so I went and bought an Adaptec AUA 1420a because there were posts suggesting it was supported in linux.  

But still no joy.  The pccardctl status shows a card in the slot, but that's it -- nothing shows up in lspci, lsusb or lshw because of it.   But I know the slot works fine.  Are there any drivers out there for any of these cards?  I now have two NEC cards and the adaptec to use as doorstops -- and in a way, the old laptops which would be much more useful if they had usb 2.

---

