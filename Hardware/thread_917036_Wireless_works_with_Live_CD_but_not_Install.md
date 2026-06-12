---
title: "Wireless works with Live CD but not Install"
date: 2008-09-11
forum: Hardware
---

### Post by lngdnalger on 2008-09-11
Hi - 
   I have ubuntu 8.04 LTS installed on my ThinkPad R40.  I started out with the Live CD, and everything seemed to work, including my Linksys WPC11 ver3 PCMCIA wireless card.  After the install, the system doesn't see the card.  No wireless networks are shown like they were using the Live CD, and I can't get it to work by manually adding the wireless info, either.  I also have a Linksys Wireless G PCMCIA card (WPC54G v3), but it wouldn't work even on the Live CD
   This may be a side issue, but I also am unable to get the auto updates, as it says it can't authenticate them (during a partial upgrade).
   Any help would be appreciated.  Happy to provide any info I may have left out.

Thanks!

---

### Post by life_s_good on 2008-09-11
What is the internal wireless card? Have you checked your 'ifconfig' or tried bringing it up ('ifconfig wifi0 up') on my R40

---

### Post by lngdnalger on 2008-09-11
Don't have an internal wireless, only internal wired, which is what I am using right now - but would rather use wireless.  "ifconfig wifi0 up" gives this:

wifi0: ERROR while getting interface flags: No such device

It apparenly only sees eth0, which I assume is my wired card.  I thought I saw when I was going from the Live CD to the install (during the reboot) that it said it disconnected eth1, which was probably the wireless.  Not sure why it would do that...

Thanks for the help.

---

