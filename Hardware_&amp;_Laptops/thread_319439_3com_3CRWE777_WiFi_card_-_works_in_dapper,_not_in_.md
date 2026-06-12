---
title: "3com 3CRWE777 WiFi card - works in dapper, not in edgy - here's how to fix it"
date: 2006-12-15
forum: Hardware &amp; Laptops
---

### Post by jamespi on 2006-12-15
OK, i upgraded to edgy and my wifi card stopped working. (It was fine under dapper).

It is the following model:

3Com Corporation 3CRWE777 PCI(PLX) Wireless Adaptor [Airconnect] (rev 02)

It's a PCI to PCMCIA Adapter board with a PCMCIA wifi card fixed into it.

I found this thread [INDENT][http://ubuntuforums.org/showthread.php?t=285733&highlight=edgy+beta+stable+wireless](http://ubuntuforums.org/showthread.php?t=285733&highlight=edgy+beta+stable+wireless)[/INDENT]

which explained what the problem was. This 3com has a "Prism" chipset. The Prism drivers in Dapper work. The Prism drivers in Edgy don't. Luckily, another set of drivers called Orinoco, do work with this card. Also there are drivers called Hostap that are an alternative to Orinoco, but we don't want to use those (i'm not sure if they work).

So you have to tell Linux not to load the Prism or Hostap drivers. Type the following:
```

sudo gedit /etc/modprobe.d/blacklist
```

then add the following lines to the bottom of the file:

```

blacklist prism2
blacklist prism2_pci
blacklist prism2_plx
blacklist hostap_pci
blacklist hostap

```

then save it.

now reboot. your wifi card should now be working. obviously it now needs configuring for your network if not already done, but that is outside the scope of this post. Hope this helps someone, as i had a hell of a job pinning this problem down with forum searches, so hopefully anyone with the same card as me will be able to find this easily.

---

