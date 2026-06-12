---
title: "Impact of disabling ipv6"
date: 2005-11-15
forum: General Help
---

### Post by canadianwriterman on 2005-11-15
Last week, there was discussion and warnings about the "consequences" of disabling ipv6 to make Firefox look up IP addresses faster. Unfortunately the string ended without anyone offering an answer.

For me, disabling ipv6 speeded up ALL programs that access the Internet, not just Firefox. So, I'm not convinced that the need to disable ipv6 is a bug in the software. If so, it's also in Opera and Synaptic. I've had no negative consequences to disabling ipv6.

That said, if there are some real consequences, I'd like to hear about them. So far, the answers I've read include:

"ipv6 doesn't work if you disable it."
"It's not a good thing to do if you rely on ipv6"

But, what do those answers mean? How do I KNOW if I rely on ipv6?

Just want to bring closure to a topic that's in this and the forums of many other distros. Thanks.

---

### Post by suRoot on 2005-11-15
IPv6 has been thrown about for years.  At present, we're using IPv4 which gives us the IP addresses that we all know and love (eg. 192.168.2.2).  IPv6 extends that by moving from 32bits to 128bits, which produces an address like 3ffe:0501:0008:0000:0260:97ff:fe40:efab.  The reason for moving to IPv6 is that there is a very limited number of IP addresses available under IPv4.  IPv6 is supposed to provide enough addresses for every person & device in the world (many times over), thereby removing the need to rely on things such as NAT.

Anyways, IPv6 has not been widely adopted, and quite frankly I have doubts that it ever will.  Some backbones are running IPv6 at the moment and, if I'm not mistaken, China migrated to IPv6 a few months ago.  But for you & me, unless you're running IPv6 on your box (and if you're unsure - you're not), it's should be safe to kill it.  All your home networking equipment uses IPv4, your ISP almost certainly uses IPv4 and the big boys up the stream know how to convert it.  If you don't know what it is, there should be no harm in getting rid of it.

---

### Post by canadianwriterman on 2005-11-15
Thank you, suRoot. That's a great explanation and makes a lot of sense.

---

