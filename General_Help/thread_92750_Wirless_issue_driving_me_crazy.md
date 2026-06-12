---
title: "Wirless issue driving me crazy"
date: 2005-11-20
forum: General Help
---

### Post by htx on 2005-11-20
Ok this is my first time running linux so please bare with me.  I got the wireless card installed it's the linksys wmp54g ver 1.2 but I used a ver 2.0 driver, but Im pretty sure that doesn't matter.  

Here is the wierd problem I can ping the router and the other computers in the house but I can't get out on the internet.  I tried changing the DNS, is there a firewall in Ubuntu?

Thanks,

Lou

---

### Post by xavierh on 2005-11-20
[QUOTE=htx]Ok this is my first time running linux so please bare with me.  I got the wireless card installed it's the linksys wmp54g ver 1.2 but I used a ver 2.0 driver, but Im pretty sure that doesn't matter.  

Here is the wierd problem I can ping the router and the other computers in the house but I can't get out on the internet.  I tried changing the DNS, is there a firewall in Ubuntu?

Thanks,

Lou[/QUOTE]
check to see if you have a package called firestarted installed.

---

### Post by htx on 2005-11-20
No I did a search for it and it doesn't come up with anything, and it doesn't find it in the terminal either.

Lou

---

### Post by taurus on 2005-11-20
Look in System --> Administration --> Networking to make sure you have configured it, wlan0, correctly...

---

### Post by htx on 2005-11-20
Ok in properties I have it set with a static Ip

192.168.1.108
255.255.255.0
192.168.1.1

The DNS Server I used what the windows machine gives me wich is
192.168.1.15 then on the search domains it automatically gives me my provider which is cfl.rr.com

I can't ping anything outside of my network like google.com or anything.  I tried outside DNS that a friend gave me but that still didn't work.

Lou

---

### Post by m0biu5 on 2005-11-20
Just as a correction, its firestarter, not started. Best of luck with your wireless issues - I had them as well. =/

---

### Post by htx on 2005-11-20
[QUOTE=m0biu5]Just as a correction, its firestarter, not started. Best of luck with your wireless issues - I had them as well. =/[/QUOTE]


Yeah I tried firestarter firestart firestarted

---

### Post by jliedeka on 2005-11-20
Have you tried getting your IP from DHCP?  Normally all the right stuff gets set up.  You could also try throwing some manual commands at your DNS server.

My local setup uses DHCP.  My router (SMC) uses 192.168.2.1 which relays DNS to my ISP as well as being the gateway.  Are you doing DNS on a local box or just doing a pass through to your ISP?

     Jim

---

### Post by htx on 2005-11-20
I got it all to work, Thanks for all the help.  I re-installed ubuntu and it seemed to work.

Lou

---

### Post by thezerogroup on 2005-11-21
Fixed it the microsoft way . . .very nice!

---

### Post by htx on 2005-11-29
[QUOTE=thezerogroup]Fixed it the microsoft way . . .very nice![/QUOTE]

When all else fails that's the best way :)

---

