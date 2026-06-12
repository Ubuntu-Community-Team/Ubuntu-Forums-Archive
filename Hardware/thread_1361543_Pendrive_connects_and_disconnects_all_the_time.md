---
title: "Pendrive connects and disconnects all the time"
date: 2009-12-22
forum: Hardware
---

### Post by GDR! on 2009-12-22
Hi,

I got a new pendrive some time ago. I plugged it in, tested - it worked - and, because I don't trust in factory pre-format, did something like:

```
mkfs.vfat /dev/sdc
```

After it finished, the pendrive is not usable anymore. When I plug it, KDE notifies me that it's plugged, then that it's unplugged and so on. This is tail -f /var/log/messages:

[http://gdr.pastebin.pl/15278](http://gdr.pastebin.pl/15278)

I would appreciate any ideas on how to "unbrick" my drive.

---

