---
title: "DNS problem?"
date: 2005-11-30
forum: General Help
---

### Post by thisisme on 2005-11-30
Hi,

I have just installed Ubuntu and when I start firefox and type in a url it goes nowhere. I started a terminal session and pinged a url and it worked fine, it just seems that firefox doesn't. What have I done wrong?

---

### Post by teaker1s on 2005-11-30
type in firefox address bar 

about:config

search 

ipv6

and disable it

---

### Post by Edit on 2005-11-30
You may be right when you suggest DNS also, I had this problem only this morning.

To add your DNS settings to Ubuntu, go to: 

```

System > Administration > Network settings

```

Click the DNS tab, hit ADD then add your DNS settings in there.  If you don't know them, they should be under the support section of your ISP's website.

-Edit

---

### Post by teaker1s on 2005-11-30
note if you use DNS with DCHP you need to edit system file to keep dns server address constant with static it will stay the same
also make sure you enable UPnP in your router

---

### Post by thisisme on 2005-11-30
[QUOTE=teaker1s]type in firefox address bar 

about:config

search 

ipv6

and disable it[/QUOTE]


Thanks, that did the trick!

---

### Post by meles² on 2005-12-25
> type in firefox address bar

about:config

search

ipv6

and disable it

This helped me too- whew, **Thanks!!**
(set network.dns.disablelPv6 to true)

---

