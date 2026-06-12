---
title: "REALTEK Wireless Card not working"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by sam1967 on 2005-06-22
lspci shows

0000:00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 
802.11b MAC (rev 20)

it works great under windows 2000.

any ideas how to get it working under hoary kernel 2.6.10-5-386

---

### Post by hw-tph on 2005-06-22
The RTL8180L is not yet supported in Linux. You can, however, use the ndiswrapper workaround to use it if you don't care about ndiswrapper [being evil](http://acx100.sourceforge.net/ndis_cludge.html). ndiswrapper installation and usage is outlined in the wiki.


Håkan

---

### Post by sam1967 on 2005-06-22
thats fine. ill use something that is.

any PCI 11 mb suggestions ?

---

### Post by der_joachim on 2005-06-22
[QUOTE=hw-tph]The RTL8180L is not yet supported in Linux. You can, however, use the ndiswrapper workaround to use it if you don't care about ndiswrapper [being evil](http://acx100.sourceforge.net/ndis_cludge.html). ndiswrapper installation and usage is outlined in the wiki.
[/QUOTE]

No offense, but if it were not for NDISwrapper, I would have had to wait another five years for my wireless card to work. Either that or I would have had to buy a crappy Prism card or something. There is something fundamentally wrong about blaming the NDISwrapper project for not having Linux native drivers available. It's like blaming charity institutions for poverty and calling _them_ evil. 

Right. Back on topic: try NDISwrapper. Be sure to read [http://ndiswrapper.sourceforge.net/phpwiki/index.php/InstallDebian](http://ndiswrapper.sourceforge.net/phpwiki/index.php/InstallDebian). My crappy Asus card works better under Linux with NDISwrapper than it does under Windows.

---

### Post by az on 2005-06-22
Ndiswrapper is not eveil. It is gpl.

The fact that the windows drivers are binary-only and closed source is.

You can always just look at is as though it is firmware and take a stance about it from that point of view...



But by all means!  When yo buy a new card, make a point of finding one that has native linux support.  Make you opinion known to the salespeople at your local store...

---

