---
title: "Network problems w/ Feisty &amp; Realtek 8139 Ethernet controller"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by mattengland on 2007-10-16
I installed Feisty 7.04 on a system that already had 6.06.1 and Windows installed with no problems, and the ethernet network worked fine.

However, the Feisty network did not work at any point of the install, and it still doesn't work.  An eth0 does exist, but "dhclient eth0" does not work.  But to repeat, Windows and 6.06.1 works just fine on the exact same hardware and network configuration.

What can I do to debug this situation?  How can I provide more data, ie, which data should I provide?   Are there some drivers I can add to the system (which is a little tougher to do since the network doesn't work...of course).

A little info:  'ifconfig -a' shows eth0, but not in /etc/network/interfaces.

Thanks for any help,
-Matt

---

### Post by mattengland on 2007-10-17
I should also mention that I installed Feisty 7.04 from an "alternate" cdrom because the regular Desktop one doesn't not install properly (presumably because of my nVidia dual-monitor system).

---

### Post by HughR on 2007-10-20
You really have not given enough information.

Perhaps dmesg output, especially where eth0 is mentioned, would be useful.

I found your message because I was looking to solve a network problem after installing 7.10.  The solution for my problem is here: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by mattengland on 2007-10-21
Thanks very much for that reference, that solution solved my problem as well.

---

