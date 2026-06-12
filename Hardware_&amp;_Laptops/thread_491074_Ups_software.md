---
title: "Ups software"
date: 2007-07-03
forum: Hardware &amp; Laptops
---

### Post by gouzos on 2007-07-03
I have a small UPS that ran the software Winpower and connected via USB.

Any idea what I should do to control it in UBUNTU(automatic shutdown and stuff like that)?

---

### Post by gborzi on 2007-07-03
It depends on the UPS brand. For APC there is the apcupsd package, for other brands you can try nut, it's in the repositories. Look here [http://www.networkupstools.org/]("http://www.networkupstools.org/") to check if your UPS is supported.

---

### Post by gouzos on 2007-07-03
It appears it is compatible (Mustek Powernust600)

However I can't find it in the add applications menu.
Should I install the Debian version from their site?

---

### Post by gouzos on 2007-07-03
Ok.
So I installed it through Synaptic.(I don't know why Add/Remove Applications doesn't find it)

How do I use it though?
I can't find it in my toolbar.

---

### Post by gborzi on 2007-07-03
IIRC you have to edit files in /etc/nut or perhaps /etc/ups. Read the README.Debian in /usr/share/doc/nut .

Regards.

---

### Post by gouzos on 2007-07-03
Sorry to be nagging, but I don't understand a thing.
I tried knutclient but i can't configure it right.

---

### Post by Gabn on 2007-07-07
> **gouzos said:**
> 
I tried knutclient but i can't configure it right.

Knutclient is only a frontend. so you need to get it working last. 

I got my ups working using nut [http://ubuntuforums.org/showthread.php?t=491994](http://ubuntuforums.org/showthread.php?t=491994) 

I followed the guide on this site [http://www.engadget.com/2006/07/25/how-to-network-your-ups/](http://www.engadget.com/2006/07/25/how-to-network-your-ups/) is should help you expect just ignore the part about a WINnut replace WINnut with Knutclient it took me a 2ish days to work mine out i spent 1 day trying to get the crappy provided software to work.

---

