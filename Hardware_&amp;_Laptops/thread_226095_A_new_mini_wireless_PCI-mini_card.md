---
title: "A new mini wireless PCI-mini card"
date: 2006-07-30
forum: Hardware &amp; Laptops
---

### Post by joshier on 2006-07-30
Hello

A member on here made me realize I am able to swtich my broadcom wifi card with an atheros one!

I'm looking on ebay now (I'm in the UK) and I'm wondering how much I should pay for them, and how well they are supported?

I'd also like to know if they are the best supported linux cards out there?.. I won't have to install anything to get it working will I?


Cheers.

---

### Post by stalker145 on 2006-07-31
Regretfully, I do not recall where I got my Atheros from, but I do remember that I paid $30USD for it delivered. My mini-pci is a beauty. I plugged the card in and did a fresh install of the OS and everything 'just worked'. Range is excellent, throughput is good, and even the basic wireless stuff that comes with Ubuntu works great for configuring.
I don't know anything about other hardware as I'm just over a month old when it comes to using Linux.

---

### Post by joshier on 2006-08-04
Thanks.. I looked on ebay for a atheros wifi mini pci card, but I can only find roughly 15 of them from germany, china..

---

### Post by joshier on 2006-08-04
OK, forget I said that.. I found a bunch of them, but I'm not sure what's best!

AR5212A, AR5002X, 5213A, AR5005GS AR2413, AR5004X AR5213,AR5004X, AR5004G AR5213, AR5006XS.

---

### Post by maestrobwh1 on 2007-08-28
was the second best upgrade to my laptop [acer aspire 3005 LCi] , 

I got this one [URL="http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=250155747871&ssPageName=STRK:MEWN:IT&ih=015"]http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&rd=1&item=250155747871&ssPageName=STRK:MEWN:IT&ih=015
[/URL]
I was opposed to replacing working hardware for two distributions, and the restricted manager in Feisty and now Gutsy ran the broadcom fine, but whenever the kernel updated, my settings seemed not to carry over.  Then I changed my mind about replacment and so far I am glad I did.

$28.90 (with shipping) spent on an atheros mini pci card found on e-bay [just type in "atheros mini pci"} and it even came with the terminal ends for the two wires to light up the front panel showing that it was working.  Two screws removed from the panel cover, popped the broadcom and put the atheros in its place.  Booted and poof it worked.

There seems to be an effort on the part of the restricted-manger to enable its own driver - and it only seemed to run the card at 11 MBPS.  I unchecked it and rebooted and it seems to be falling back on the native madwifi ubuntu driver. I much prefer open source if it works the same or better.  I am using Gutsy, so I am not sure how it will fare in other Ubuntu's.  Atheros has always had good support.

The first best upgrade was getting an 8 cell battery, but that is more of a time of use as opposed to farting around with all the things needed to get the bcm 4318 to work... at either reduced bandwidth [restricted-manager fwcutter method], or having all wireless reporting at 100% signal [ndiswrapper].

I have been grateful for the work others have done with these two methods.  They DO work with otherwise unusable hardware.

A bonus for replacement seems to be the improved range extended in both (K)ubuntu, and XP - dual OS and the driver was found for XP on a first hit on Google.

---

