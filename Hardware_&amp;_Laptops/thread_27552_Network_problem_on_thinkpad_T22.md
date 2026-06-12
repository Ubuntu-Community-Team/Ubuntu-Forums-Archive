---
title: "Network problem on thinkpad T22"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by erpagnotta on 2005-04-16
Hi all!
I have a network problem on my laptop connected through one router ADSLI ,my configuration is apparently OK, so I see other PC connected to the router but I'm not able to browse internet with firefox or epiphany but I can ping some host like [www.google.it.I](www.google.it.I) set the default Gateway to the router IP.
The chipset is a intel 82577.
I have same problem with knoppix 3.3/3.8 but with a gentoo-live cd I can browse
internet with links text browser ](*,) .

---

### Post by hagman on 2005-04-16
Sounds like you have a problem with your nameserver (DNS).
Do you have a static IP address? So check /etc/resolv.conf for the appropriate nameserver entries. Depending on your ADSL router, you can

- add the router's IP address or
- your providers IP address

as your nameserver entries.

Cheers,

Helge

---

### Post by erpagnotta on 2005-04-16
I have already put router IP address in /etc/resolv.conf ](*,)

---

### Post by hagman on 2005-04-16
Ok, then add your ISP's name server addresses to resolv.conf.

---

### Post by arctic on 2005-04-16
[QUOTE=hagman]Ok, then add your ISP's name server addresses to resolv.conf.[/QUOTE]
 take a look here. [http://ubuntuforums.org/showthread.php?t=5690](http://ubuntuforums.org/showthread.php?t=5690)
:)

---

### Post by r00t on 2005-04-17
This definitely sounds like some sort of misconfiguration.  I run a T22 ThinkPad without issue.

Feel free to post your network settings so we can assist you.

Regards,

Mark

---

