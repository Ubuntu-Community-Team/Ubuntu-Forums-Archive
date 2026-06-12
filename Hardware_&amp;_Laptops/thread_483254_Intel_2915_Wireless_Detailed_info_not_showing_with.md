---
title: "Intel 2915 Wireless: Detailed info not showing with ethtool"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by sheilnaik on 2007-06-24
Two network cards in my system:
1. eth0: Wired NIC
2. eth1: Wireless Intel 2915

ethtool shows detailed info for eth0, including supported link modes, speed, wake-on-lan, etc.  However, ethtool shows only the following for eth1 (my wireless card):

```
Settings for eth1:
Link detected: yes

```

I'm asking because I'm trying to get wake-on-lan working with my wireless card, but before I can do that, I need to at least be able to see the ethtool info.  Any suggeestions?

---

