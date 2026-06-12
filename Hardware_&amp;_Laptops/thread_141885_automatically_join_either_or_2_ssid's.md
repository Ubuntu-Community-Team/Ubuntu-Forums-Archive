---
title: "automatically join either or 2 ssid's?"
date: 2006-03-09
forum: Hardware &amp; Laptops
---

### Post by jjf on 2006-03-09
I've got my wireless PCMCIA card working at home and at work.  To do this, I had to manually edit the /etc/network/interfaces file.  Right now I have two "backup" files -- interfaces_home and interfaces_work -- and I have to 
```
sudo cp /etc/network/interfaces_work /etc/network/interfaces
```
When I first start up at work and do the same with interfaces_home at home.  

What I'd like is for Breezy to automatically detect and join any SSID that it's allowed to.  So if I take my laptop to the coffee shop, for example, right now I'd have to somehow figure out what the SSID was (and I'm not sure how I'd do that) and then edit my interfaces file.  I want Breezy to just notice an open network and put it in a list somewhere so I can choose to join it.  Is this possible?

Thanks.

---

### Post by jjf on 2006-03-14
any ideas?

---

### Post by jrjazzman on 2006-10-05
I'd like to be able to do this also.

---

