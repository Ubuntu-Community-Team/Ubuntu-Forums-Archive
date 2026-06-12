---
title: "Migrating Soft Raid (mdadm) from Debian to Ubuntu"
date: 2009-05-02
forum: Installation &amp; Upgrades
---

### Post by kobari on 2009-05-02
Hi All,

I currently have a Debian Server with 8 MD partitions (backed by 2 identical hard disks). MD1 partition is used for root dir, and others (MD2-MD8) have user data files.

I would like to install Ubuntu Desktop on this machine, and while doing so I want to reformat MD1 but keep all other partitions intact. Just to clarify, I said "upgrade", but what I will do is to do a fresh install of Ubuntu (meaning I would like to format it) on MD1.

Is there anything special I should be doing during installation? For example, should I just define MD1 during installation but not touch MD2-MD8 and use mdadm to auto-detect these? Or will ubuntu auto detect all of these soft-raid partitions and let me format only MD1? 

In summary, would it be possible to do this without formatting MD2-MD8 partitions? 

Thanks.

---

