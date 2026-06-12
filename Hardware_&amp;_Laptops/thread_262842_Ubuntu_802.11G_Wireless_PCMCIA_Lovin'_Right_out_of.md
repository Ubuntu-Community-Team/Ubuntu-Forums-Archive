---
title: "Ubuntu 802.11G Wireless PCMCIA Lovin' Right out of the box for $17.49"
date: 2006-09-22
forum: Hardware &amp; Laptops
---

### Post by Ziptar on 2006-09-22
First off I am NOT affilated with this company in any way...

I just wanted to share, I figure this would be very helpful to Laptop wireless users..

Last week I was Given a Dell Lattitude CPx Laptop, this was great because I gave up my Compaq Laptop that I had Ubuntu on so my Kids could have a PC.. anyway...

The problem with the CPx is that is has NO built in networking what so ever... In my searching around for a Cheap WiFi PC Card I found this [Chiefmax RT2500 802.11G Wireless PCMCIA Card For $17.49 with FREE Shipping]("http://3btech.net/ch5480wipcne.html") It is Ralink RT2500 based, I have read about the good and the bad with RT2500 PCMCIA Cards and Breezy. I figured it was worth a roll of the dice for $17.49 at my door.

I ordered it Sunday night, got a ship notification Monday evening it arrived yesterday evening. The card I received looks different than the one pictured, the label is pink and not blue but it still has the generic "Wireless 11G 32Bit PCMCIA Adapter" on the label and it's an Ralink RT2500 Chipset.

I set up the MAC in my router put it in the bottom PCMCIA slot and installed Ubuntu.. It didn't work, not detected, I was bummed, then I realized the CPx has on Type I slot and one Type II. I put the card in the top Slot and reinstalled (probably didn't need to do a total re-install). 

IT WORKS!!! It was detected by the install the second time, I assume it's because the top slot is the Type II Slot and that's what this card wants. I put my Networks ESSID in the properties for the card in Networking  Manager and I was off and running. I modified /etc/network/interfaces for auto ra0 (actually it was already in there at the bottom, so I just moved it to the top.) rebooted and the network was connected at boot. 

I ran the update manager, downloaded and installed 215 updates without issue. I rebooted, opened firefox and and came here to make this posts so it seems to be working just fine.

I just wanted to share after reading about allot of PCMCIA / RT2500 WiFi Card issues that I stubled across a cheap one that works out of the box with 6.06's default installed driver.

I hope this helps somebody, or if you buy one and it doesn't work for you.. Sorry please don't get mad at me..

---

### Post by xyz on 2006-09-22
I like to hear about things that work....:D  :D 
Happy Ubuntu to you!

---

### Post by Ziptar on 2006-09-23
Just an update... I have been using it for just over 24 hours now, downloaded and installed easyubuntu, lots of packages, and lots of surfing the web...

No issues at all, it's just working...

---

