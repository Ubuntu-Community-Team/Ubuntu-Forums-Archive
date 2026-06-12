---
title: "ndiswapper wep and connection manager"
date: 2005-12-28
forum: Hardware &amp; Laptops
---

### Post by nrune on 2005-12-28
here is some strangeness for you folks to help me out with. 

Toshiba laptop a15:s129 broadcom 802.11g using ndiswrapper

Okay so I am at the hotel, they give me the wep key and say enjoy.

I put the key with the ssid into the wireless network manager 1.09 hit connect and bibbidi bobbidi boo I am connected, except I am not connected. 

The wireless manager says that all well with the world and I have 5 bars

No joy, ping says no network connection. 

Put the key in System > Networking >Preferences  No Joy at all, but the Network manager says I am connected. 

Confused. 

Does not work at home with my wireless router either. using ascii key, tried s: before the ascii key also.

---

### Post by seoatway on 2005-12-29
Hi

I had a similar problem here at home connecting to my Linksys router. I told the wireless manager that the key was ASCII and it said it was connected (but took a minute or so) but in fact it wasn't - if you look in iwconfig it will not have an associated ESSID. Once I told the wireless manager it was a hex key it worked fine, connected in a couple of seconds, got the ESSID and an IP address and away it went. May be worth a try, but iwconfig (run under sudo) will certainly give you a good idea what's happening.

Cheers

---

