---
title: "[SOLVED] CUPS webadmin very slow if gateway down"
date: 2008-09-15
forum: General Help
---

### Post by lil_elvis2000 on 2008-09-15
Hello all;
   My network is using a shared gateway via wireless bridge. The network is shared wirelessly throughout the building (well most of it). I have  PC's in my office and I have one XUBUNTU 8.04 server which is running CUPS 1.3.7, SAMBA, vsftp a few other utilities.

Every once in a while the wireless goes bezerk. I think it has to do with the guys running it - who just decide to reboot the access points whenever they feel like it. Anyway that's besides the point. Our wireless bridge then cannot pickup the signal very well.

I've noticed that in these situations if I am accessing the CUPS webadmin..it is very very slow. I think it may have to do with the gateway being unreachable...I also notice that the route command takes forever as well. 

This is very odd. Is CUPS trying to access a external site for some reason? How would I determine what it is doing..I've turned the firewall off and have no clue how I would log any outgoing traffic.

Oh yes. SAMBA, printing, FTP all work great when the gateway is down..which leads one to suspect the webadmin is attempting to access an external site.

I've no access to the access point/router logs so I imagine I would need to turn on a firewall?

Much advice appreciated.

Thanks.

---

### Post by lil_elvis2000 on 2008-09-17
I have passed this on to cups.org. looks like it was ignoring hostnamelookups and just attempting to access DNS to do a reverse lookup regardless.

Will be fixed in 1.4 - dunno if it will be patched in 1.3.7. How would on request that?

---

