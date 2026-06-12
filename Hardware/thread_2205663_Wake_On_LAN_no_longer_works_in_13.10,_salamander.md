---
title: "Wake On LAN no longer works in 13.10, salamander"
date: 2014-02-15
forum: Hardware
---

### Post by Pressurized on 2014-02-15
Hi

I've been using ubuntu for some time now with lots of success but recently I've come across a problem with Salamander that I can't solve myself or find information to help me on line.

The problem is with me setting up my server in the garage to start on receipt of a magic packet. This functionality appears to have been lost in the latest distro.

Whereas in quetzal and ringtail
```
sudo ethtool -s eth0 wol g
```
would complete with no errors, now I get:
```
$ sudo ethtool -s eth0 wol g
Cannot get current wake-on-lan settings: Operation not supported
  not setting wol
```

I know that there are BIOS settings to check but I have done this and wakeonlan works with quetzal and ringtail so the problem does seem to lie with salamander.

Does anybody have any advice to help me here?

Thanks

---

