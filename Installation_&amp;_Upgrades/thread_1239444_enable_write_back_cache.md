---
title: "enable write back cache"
date: 2009-08-13
forum: Installation &amp; Upgrades
---

### Post by jom2000 on 2009-08-13
How do I enable the write back cache for hard disks? It is enabled by default on sda, but on sdb "write through" is enabled by default.

I would be grateful if someone could tell me how to enable it on sdb also.

This is from dmesg, which shows what happened on boot:

sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
...
sd 6:0:0:0: [sdb] Assuming drive cache: write through

Note: It defaulted to "write through" on sdb because it is a usb drive, and in general it is a safer option for usb drives. Not in my case though, I just need to know how to change it to "write back".

---

