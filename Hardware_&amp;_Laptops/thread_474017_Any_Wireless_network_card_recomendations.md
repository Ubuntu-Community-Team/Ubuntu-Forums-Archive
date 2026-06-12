---
title: "Any Wireless network card recomendations?"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by the lemming on 2007-06-14
I'm having too much trouble with my belkin F5D7000.

Cheers

---

### Post by Bachstelze on 2007-06-14
Pretty much anything with a Ralink chipset. Those two pages hade devices lists at the end :

[http://www.openbsd.org/cgi-bin/man.cgi?query=ural](http://www.openbsd.org/cgi-bin/man.cgi?query=ural)
[http://www.openbsd.org/cgi-bin/man.cgi?query=rum](http://www.openbsd.org/cgi-bin/man.cgi?query=rum)

I thow this is for OpenBSD but those will work fine on Linux too.

---

### Post by the lemming on 2007-06-14
> **HymnToLife said:**
> Pretty much anything with a Ralink chipset. Those two pages hade devices lists at the end :

[http://www.openbsd.org/cgi-bin/man.cgi?query=ural](http://www.openbsd.org/cgi-bin/man.cgi?query=ural)
[http://www.openbsd.org/cgi-bin/man.cgi?query=rum](http://www.openbsd.org/cgi-bin/man.cgi?query=rum)

I thow this is for OpenBSD but those will work fine on Linux too.

I'm confused now.  I had a look through the top link and noticed that my network card should work.

Somehow I managed to get it to work before but I can not remember how I achieved this.

With this in mind I would like something which I can stick into my PC and works immediately.  

Any recomendations of products which work out of the box?

Cheers

---

### Post by Syke on 2007-06-14
Unfortunately the F5D7000 comes in numerous versions, all with different chipsets, and thus all requiring different drivers, some will work in Linux, some won't. You need to figure out which version you have.

---

### Post by racyrefinedraj on 2007-06-14
[madwifi](http://madwifi.org/) works out of the box in ubuntu for cards with an Atheros Chipset. They've got a compatibility page on the website with an exhaustive list. 

Myself, I use a D Link GWL 630 with no complaints.

---

