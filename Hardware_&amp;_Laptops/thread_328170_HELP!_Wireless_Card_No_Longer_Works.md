---
title: "HELP! Wireless Card No Longer Works"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by Metallinut on 2006-12-30
So I've been using Ubutu for a while now, and have been pretty happy with it.  Using various posts here, I've been able to get my wireless card working in my laptop with WPA2 and have loved it.

Now I finally got Beryl/XGL working on my laptop, and all of a sudden, my wireless card is "gone"

I can still see it in device manager.  But Edgy seems to no longer know that it's there!

It used to be device eth1, but now when I do an ifconfig -a all i get is:
```

eth0     
irda0
lo
sit0
```

So it doesn't list eth1 anymore at all!

Help!  Does anyone know where I can look to make Ubuntu see this wireless card again?
It's an internal run-o-the-mill Intel wireless card.

Thanks,

---

### Post by Metallinut on 2007-01-02
Update:

I rebuilt my laptop.  Wireless card shows up in System -> Administration -> Networking.  Now I followed a guide for installing Beryl using fglrx on an ATI card, and whoop!  No more wireless card listed.  

Now as far as I can tell, the only changes made were the repositories, and installation of beryl and emerald-themes (and whatever else gets installed).  Also, there was a change made to /etc/X11/xorg.conf.  

But why would that cause any change to the wireless hardware?!?!?

What the heck?!?  I'm going to rebuild this sucker again, and just forget about beryl, even though it kicks ***.  

Anyone else have this problem?  It had to do with beryl and an ATI card, and my wireless is an Intel 3945 a/b/g

---

