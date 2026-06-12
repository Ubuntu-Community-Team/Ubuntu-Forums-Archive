---
title: "ktorrent blacklisted port 6883"
date: 2008-07-27
forum: General Help
---

### Post by bizghetto2 on 2008-07-27
I have ubuntu 8.04 and I think since I downloaded frostwire everytime I try to download something using ktorrent it states that another port has to be used. The download stalls and never even begins to download. When I started checking the different tabs for more infortmation the bottom tab that says tracker states that port 6883 is blacklisted. How do I change the port or stop this from happening again?

---

### Post by warp99 on 2008-07-27
> **bizghetto2 said:**
> I have ubuntu 8.04 and I think since I downloaded frostwire everytime I try to download something using ktorrent it states that another port has to be used. The download stalls and never even begins to download. When I started checking the different tabs for more infortmation the bottom tab that says tracker states that port 6883 is blacklisted. How do I change the port or stop this from happening again?

It means that Frostwire, or it's daemon, is still running and has taken port 6883. You can check to see if the port is taken by opening a terminal and issuing the following:

```
netstat -l
```

If the port it not taken then the problem is with your router blocking that port for port forwarding or your ISP is blocking that port.

Edit:

If it's a port forwarding issue then use the [portforward.com]("http://www.portforward.com./") guide for your particular router.

---

