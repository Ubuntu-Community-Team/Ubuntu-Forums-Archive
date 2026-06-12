---
title: "Good wireless card for wardriving"
date: 2006-03-29
forum: Hardware &amp; Laptops
---

### Post by h3llfyr3 on 2006-03-29
Any recommendations for a card for Ubuntu that will work out of the box with breezy?

Pref one with plugs for an antenna?

ATB
-H

---

### Post by ssalman on 2006-03-29
did you check [this ]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?action=show&redirect=WirelessNetworkCards")wiki page?

Edit: Sorry missed the "wardriving" part

---

### Post by jml on 2006-03-29
For wardriving, (using Kismet and Airsnort,) you will need a card that can be placed into monitor mode.  The two cards that I have used that can do this, and are recognized by Ubuntu are the Cisco Aironet 350, and the Orinoco Gold Classic card (not the one sold by Proxim.)  The 350 is still being sold by Cisco so you should be able to find one.  The Orinoco is no longer being manufactured, so you will probably have to go someplace like eBay to find it.

Joe

---

### Post by Hairback357 on 2006-03-30
I am faced with the same problem myself. I wardrive regularly and this is the last thing holding me back from using Linux all the time. I have a Buffalo 54HP now and it doesn't work at all in Linux. I am also having problems finding a program like Winc or Netstumbler for Linux. I heard Wellenriter is good but I dont know how to install it. I am real new to Linux so I am learning as I go. 

I hope someone comes along that has an answer to this question for sure. I need a card that is 100mw or better and has a MC connecter. If I find one that works I will report back.

---

### Post by John.Michael.Kane on 2006-03-30
[http://www.wardriving.com/](http://www.wardriving.com/)

**Do This At Your Own Risk!!!!**

---

### Post by localzuk on 2006-03-30
I would recommend the Cisco model. If you buy the one without its own ariel you can attach a better one to it (which you could mount on your car roof).

---

### Post by Hairback357 on 2006-03-30
I had a Cisco 340 and ironically just sold it to a guy right before I started playing with Linux. When I bought the Buffalo card I decided it worked better than my Cisco card and sold it. The one thing I really disliked about the Cisco card was how it sat flush with the laptop. It made keeping the coax connected. It also was difficult to get the card out of the slot too. It figures I sold the cars I need though. Just my luck.

---

### Post by h3llfyr3 on 2006-03-31
I went for the cisco 350 slightly more powerful than the 340 so get a 350 if poss. I used to use a senao 2511cd under WHax which worked pretty well (as Muts the project admin uses that brand so it works out the box and is a powerful card).

The 350 aironet is going for around £15 (GBP) on ebay...

EDIT 

Just received it today and found the cisco 350 had no connections for an antenna :(
so have just bought a ORiNOCO Gold Classic from here, apparently they still have a few in stock 
and it does have a connector for an antenna (which you need or you'll get mostly beaconing packets)
[http://www.beacon-link.co.uk/pages/wireless_sale.htm](http://www.beacon-link.co.uk/pages/wireless_sale.htm)

Necessary lines in kismet.conf, your eth will prob be 1 (I have two cards)
for the cisco aironet card...

source=cisco_wifix,eth2:wifi0
enablesources=cisco

---

### Post by Hairback357 on 2006-04-05
I ordered a Cisco 350 off of eBay and it just got here today. I can now confirm that it worked right out of the box so far without any configuring . I am using it right now and it seems to work great. I will report back after I have it for a while. I shouldn't have any problems with it but if I do I will let you all know. The hunt continues for a decent scanning program though. The one I found most useful so far is KWiFi Manager but it is still a far cry from Winc or Netstumbler. There has to be a good one out there. I guess I just haven't found it yet.

---

