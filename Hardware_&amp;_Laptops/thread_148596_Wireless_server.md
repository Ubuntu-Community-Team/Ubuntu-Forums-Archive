---
title: "Wireless server"
date: 2006-03-22
forum: Hardware &amp; Laptops
---

### Post by BeachBum on 2006-03-22
Hello everyone!

I'm looking to put together a wireless microatx server to act as a router/file server on my lan.  My problem is this: I am a college student who lives off campus and the "high speed" internet in my apartment runs at real-world 56k speeds.  My campus wireless internet is a shared T3 connection, and even at peak usage times I can get 600k+ speeds.  I am planning to roam around outside with my laptop to see how far the signal can get to my place.  The nearest antenna I've seen on a building is about 3 blocks away.  

My question to you guys is: 1. can Ubuntu be configured to act as a signal repeater with two wifi cards?  2. Will a high gain directional antenna help in picking up the signal?  3. Can anyone recommend inexpensive wireless hardware that plays nicely with Ubuntu?

Thanks!

---

### Post by gnu2tux on 2006-03-27
1. Yes, you should be able to use it as a repeater:

echoing 1 into either 

/proc/sys/net/ipv4/conf/ethX/forwarding
/proc/sys/net/ipv4/ip_forward

where ethX is the card you want to forward through, will switch on ip forwarding, meaning you can route traffic through that interface onto somewhere else.

2. Will a high gain directional antenna help in picking up the signal?

Probably. These 9db antennae are often good, but do your homework first!

3. Can anyone recommend inexpensive wireless hardware that plays nicely with Ubuntu?

Cisco Aironet 350 (or 340 cheaper) series PCI and PCMCIA cards.
You can get them from Ebay for around 20-25 pounds and are rock solid, plug and play 802.11b cards. You will not go wrong with them in any situation.

For more information, see the guide I put together:

[http://www.linuxnewbieguide.org/ht-wififallback.php]("http://www.linuxnewbieguide.org/ht-wififallback.php")

Hope this helps,

Ali.

---

