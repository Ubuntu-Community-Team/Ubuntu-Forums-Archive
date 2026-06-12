---
title: "Intel H55 chipset support"
date: 2010-01-19
forum: Hardware
---

### Post by lptr on 2010-01-19
Hi out there,

As I could not find any references for it I would like to know if there is already support for H55 chipset. Especial interest for board Intel DH55HC or DH55TC in combination with i5-661 and its built in graphics capabilities? 

9.10 ? / 10.04 ? / Neither ?

Thanks

rob*

---

### Post by lukeiamyourfather on 2010-01-19
I assume it would function in 9.10 but I don't have the hardware to confirm this. If Google is unable to procure an answer, take a flash drive with Ubuntu 9.10 into a electronics shop and give it a shot on a machine with a Core i5. :-$

---

### Post by iskarion on 2010-01-19
Not sure about this, as I'm currently also looking for an answer to that question.
  
The Clarkdale IGP is officiall supported as of kernel 2.6.33
Ubuntu 10.04 will be based on 2.6.32.

But at least it seems to partly work even in Ubutnu 9.10 according to this post in a german Ubuntu forum:
[http://forum.ubuntuusers.de/topic/intel-clarkdale-i5-mit-h55-chipsatz-und-video/](http://forum.ubuntuusers.de/topic/intel-clarkdale-i5-mit-h55-chipsatz-und-video/)
The User reports that it sort of works after upgrading the intel driver to 2.10 and disabling compositing. Though he has issues with slow video playback. There is also an Xorg.log attached to that post, so you might be able to get some useful information from that.

---

### Post by lptr on 2010-01-20
:) seems we have both similar targets :)

Some sources (none mentioning in one word support of builtin graphics for Ubuntu nor Debian) - obviously we have to wait some time to switching over to i5.

[http://www.intel.com/cd/products/services/emea/deu/motherboards/desktop/DH55HC/overview/436112.htm](http://www.intel.com/cd/products/services/emea/deu/motherboards/desktop/DH55HC/overview/436112.htm)

[http://www.tomshardware.com/reviews/intel-clarkdale-core-i5-661,2516-2.html](http://www.tomshardware.com/reviews/intel-clarkdale-core-i5-661,2516-2.html)

(German, too)
[http://www.heise.de/newsticker/meldung/Startschuss-fuer-Intels-neue-Doppelkerne-894398.html](http://www.heise.de/newsticker/meldung/Startschuss-fuer-Intels-neue-Doppelkerne-894398.html)

rob*

---

### Post by Kitemolchi on 2010-01-23
> **iskarion said:**
> 
But at least it seems to partly work even in Ubutnu 9.10 according to this post in a german Ubuntu forum:
[http://forum.ubuntuusers.de/topic/intel-clarkdale-i5-mit-h55-chipsatz-und-video/](http://forum.ubuntuusers.de/topic/intel-clarkdale-i5-mit-h55-chipsatz-und-video/)
The User reports that it sort of works after upgrading the intel driver to 2.10 and disabling compositing. Though he has issues with slow video playback. There is also an Xorg.log attached to that post, so you might be able to get some useful information from that.

I also have a DH55TC with i5-661 and used onboard graphic. KDE4 compositing works fine with current 9.10 but video playback and scrolling is extremly slow. At least it didn't crash yet.

---

### Post by lptr on 2010-01-25
Thanks for reply 

> **Kitemolchi said:**
> I also have a DH55TC with i5-661 and used onboard graphic. KDE4 compositing works fine with current 9.10 but video playback and scrolling is extremly slow. At least it didn't crash yet.

How about audio support?

rob*

---

### Post by achiav01 on 2010-01-26
check [https://wiki.ubuntu.com/Intel_DH55TC](https://wiki.ubuntu.com/Intel_DH55TC)

---

