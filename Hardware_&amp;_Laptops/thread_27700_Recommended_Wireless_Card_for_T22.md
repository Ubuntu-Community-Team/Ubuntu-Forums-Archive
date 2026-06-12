---
title: "Recommended Wireless Card for T22"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by r00t on 2005-04-17
Greetings everyone,

I'm looking to purchase a wireless card for my IBM T22.  What is recommended for ease of use?  Are there certain brands that are better supported than others?

Thanks,

Mark

---

### Post by heimo on 2005-04-17
About year ago I was in similar situation and did lots of searching to find good card. This is not the cheapest one on the market, but at least I can confirm that it's possible (and as far as I remember, easy) to install on Linux. "3COM OffiiceConnect 11g PC Card", model name: 3CRWE154G72

If I remember correctly, there wasn't WPA support, I don't know what the current situation is. This was with the kernel available in kernel, not the proprietary drivers (if there even exists one).

Here's list of cards to avoid:
[http://www.leenooks.com/12]("http://www.leenooks.com/12")

Hmm.. there's at last someone who got it working in Ubuntu and one who didn't: 
[http://ubuntuforums.org/showthread.php?t=11273]("http://ubuntuforums.org/showthread.php?t=11273")

I had it in Debian Sid.

I'll post couple good sites if I can find them.

This is one of them (prism54 driver is in kernel)
[http://prism54.org/supported_cards.php]("http://prism54.org/supported_cards.php")
 > 
 I can recommend you just not buy a prism 802.11g based chipset for now.  :(

---

### Post by tomchuk on 2005-04-17
If you don't need 802.11g, the Orinoco Gold is the best card you can get. Powerful, external antenna jack, awesome Linux support. Also, If you have a free miniPCI slot and built-in WiFi antennae, IBM had a Prism2 card for the T2x series that would work, if you can find one on eBay. Also great linux support, with the added bonus that you don't need to worry about snapping the antenna off of an external card.

---

### Post by mendicant on 2005-04-17
I prefer the Cisco Aironet 802.11b cards to the Orinoco ones--I've occasionally run into weird behavior with the Orinocos in an ad-hoc network.  I don't know if they're still sold, though--they do have an a/b/g card, which looks to be supported by the madwifi driver (in restricted-modules), but I've never tried it.

---

### Post by tomchuk on 2005-04-17
I've got an Aironet in my t40, I like it, but the way it randomly channel hops in rfmon mode is a pain.

---

### Post by mendicant on 2005-04-17
That's funny.  The channel hopping and scanning was the problem I was having with the orinocos.

---

### Post by sheol on 2007-09-06
Dlink works well

---

