---
title: "IP Address Prompt During Install"
date: 2005-12-17
forum: Installation &amp; Upgrades
---

### Post by Fermanagh on 2005-12-17
During the install of edubuntu, there is a screen that asks you for the IP Address of the machine. I don't have a clue what to type in at this point. If I type in random numbers like 123.123.123.123  , the process continues, but I am not sure that the install will complete OK. 

What is the correct procedure to get the IP Address of the machine? I am installing where I completely overwrite the hard drive (no partitions). 

There is no OS on the machine before I install edubuntu.

Is it OK to input dummy numbers like 1.2.3.4  ??

---

### Post by afhp on 2005-12-17
There are specific address ranges that have been set aside for machines/networks that shouldn't be seen from the outside. (They're called "non-routable".)

There are also two reserved addresses on any range that you can't use for any specific machine, those are the ones ending with .0 and .255

The most common non-routable range for a single machine or a small LAN is 192.168.*

So you can give your machine any address that start with 192.168, like 192.168.1.10 for example ; but not 192.168.1.0 nor 192.168.1.255.

If this machine is connected to a broadband modem, chances are you could use DHCP -- in which case your machine gets an address from the modem when it starts; check the modem's manual.

---

### Post by Fermanagh on 2005-12-17
Afhp,
Thanks for the really helpful information. I printed out your post and will keep it handy the next time I do an install.

---

### Post by afhp on 2005-12-17
You're welcome. 

I encourage you to have a look at RFC 1918 which gives the detail. A bit dry and technical, but that's where it comes from. (RFCs or Request For Comments are, simply speaking, where the rules and definitions of how things internet-related work are born and evolved.) RFCs are available everywhere, [http://www.cse.ohio-state.edu/cgi-bin/rfc/rfc1918.html]("http://www.cse.ohio-state.edu/cgi-bin/rfc/rfc1918.html") among others.

There's also a bunch of HOWTO, particularly on installation and networking, that will be of interest. You can find them at the [Linux Documentation Project]("http://www.tldp.org/") :

[http://www.tldp.org/HOWTO/HOWTO-INDEX/networking.html]("http://www.tldp.org/HOWTO/HOWTO-INDEX/networking.html")

All these RFCs and HOWTOs might be a little overwhelming for a beginner ; but if you stick to it, it's the best way to learn.

---

