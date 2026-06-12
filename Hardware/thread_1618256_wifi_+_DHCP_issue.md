---
title: "wifi + DHCP issue"
date: 2010-11-10
forum: Hardware
---

### Post by gomer on 2010-11-10
On a laptop that I had upgraded from 9.10 to 10.04, I started having trouble connecting to wireless networks. After a little bit of troubleshooting, I was able to determine that the failure was with the DHCP client. Essentially, if I manually configured all my wireless connections with a static IP, I could associate and connect. But if I let NetworkManager continue to use the "Automatic" settings, it would simply tell me I could not connect. I could specify an arbitrary static IP and then manually invoke dhclient3 to obtian a valid address from the network. This was of course rather inconvenient, so I decided I would kill 2 birds with one stone (hopefully) and also upgrade to 10.10, but instead of an upgrade, for fear of keeping a potentially broken configuration, I did a fresh install. 

So, now, here I am with a shiny new install of Maverick, and I am still unable to connect to wireless networks as long as I am relying on DHCP. I have not yet gone so far as to do some packet captures and debugging / logging at a Linux-powered Access Point. But, I have confirmed, from the laptop, the same behaviour. I can associate, and if I provide myself with an arbitrary IP address, things are fine, and I can later manually invoke the dhcp client. There seems to be some failure in either NetworkManager, or potentially with my hardware (though this seems rather unlikely). 

Does anyone here have any ideas?

---

### Post by faflu on 2011-01-31
I have no idea how to fix it, but I have a similar problem with wifi + dhcp.
I have U.10.10 with edimax usb wifi card. It uses rt73usb module. I connect using network manager. My router is belkin N150. Until recently sometimes after computer's startup wifi was up and sometimes I needed to turn network off (in nm) an on again to make it work. Sometimes I needed to replug the nic to make it work. But now I have the same problem as you have. I checked kernels, but it doesn't make any difference. Perhaps just this edimax + rt73 is a piece of crap.

---

