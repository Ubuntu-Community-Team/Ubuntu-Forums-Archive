---
title: "dhcp and port forwarding..."
date: 2008-09-29
forum: Hardware
---

### Post by hardyn on 2008-09-29
I am currently using a dlink 624 wifi router, fairly happy with it.  does anybody know if there is a way to set up port forwarding on that router so the forward will follow the computer, not the explicit  ip address?

as there are a few people in the house, my ip address isn't always the same.  While its not hard to change the forward, it is however a little annoying.

Is there a wifi router that is more intelligent (or maybe its me that need to be more intelligent) and will follow the computer even if the dhcp server in the router assigns me a different ip from time to time.

Thanks for any help.

---

### Post by jms1989 on 2008-09-29
One thing to do would be to set your computer to a static ip address like, 192.168.x.10. The are no routers, that I know of, that can track the computer by host name (computer name).

---

### Post by olejorgen on 2008-09-29
Probably not. Maybe some router can forward based on the mac address. (one that runs linux could probably to it with iptables)

Anyway, easiest thing is proably to set the dhcp lease time as high as possible. (Configured on the router)

---

### Post by shaggy999 on 2008-09-29
On a previous router I had eventhough it was dhcp you could set it up so that the dhcp service always handed the same IP address to a certain mac address and reserved that IP for that mac address. Then I would just go in and set port forwarding to that ip address. I think it was a linksys wrt router.

---

