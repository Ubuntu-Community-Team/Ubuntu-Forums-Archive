---
title: "Built in SD card reader help. HELP!"
date: 2009-04-10
forum: Hardware
---

### Post by tabarnackle on 2009-04-10
I am having nearly zero luck for my problem by googling, but the problem i have is i really dont know how to use the card reader. i mean, in ubuntu.

Im trying to mount up a sony memory card and put the pics on my harddisk. where do we begin? HELP!

---

### Post by cariboo on 2009-04-10
Could you paste the output of the following command in your next post. Open an Application-->Accessories-->Termainl and type:

```
dmesg | tail -n10
```

after you have plugged your memory card in.

Jim

---

### Post by tabarnackle on 2009-04-11
[   58.652121] CPU0 attaching sched-domain:
[   58.652129]  domain 0: span 0-1 level MC
[   58.652133]   groups: 0 1
[   58.652143] CPU1 attaching sched-domain:
[   58.652147]  domain 0: span 0-1 level MC
[   58.652151]   groups: 1 0
[   95.524123] NET: Registered protocol family 10
[   95.526333] lo: Disabled Privacy Extensions
[   95.527382] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  106.220087] ath0: no IPv6 routers present

---

