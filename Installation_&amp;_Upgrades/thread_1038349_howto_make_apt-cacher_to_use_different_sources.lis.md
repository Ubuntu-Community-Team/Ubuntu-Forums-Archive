---
title: "howto make apt-cacher to use different sources.list?"
date: 2009-01-12
forum: Installation &amp; Upgrades
---

### Post by derekshaw on 2009-01-12
Is there a way to have apt-cacher use its own sources.list?

It occurred to me today, while waiting for some updates from a very slow Canadian repository server, that I had already been through this when I upgraded the apt-cacher host earlier in the day.

Basically, the files get downloaded twice in my shop:
once for the apt-cacher host; 
once when a machine updates from apt-cacher.

So, is there a way to have it happen only once?  Say, to have the apt-cacher host attempt to update from apt-cacher itself?  

This would, to my thinking, mean that apt-cacher would have to use a sources.list file separate from /etc/apt/sources.list.

I can't find anything in the docs about what apt-cacher uses for its sources.

Please let me know if you've done something like this.

---

### Post by Skip Da Shu on 2009-05-28
> **derekshaw said:**
> Is there a way to have apt-cacher use its own sources.list?

It occurred to me today, while waiting for some updates from a very slow Canadian repository server, that I had already been through this when I upgraded the apt-cacher host earlier in the day.

Basically, the files get downloaded twice in my shop:
once for the apt-cacher host; 
once when a machine updates from apt-cacher.

So, is there a way to have it happen only once?  Say, to have the apt-cacher host attempt to update from apt-cacher itself?  

This would, to my thinking, mean that apt-cacher would have to use a sources.list file separate from /etc/apt/sources.list.

I can't find anything in the docs about what apt-cacher uses for its sources.

Please let me know if you've done something like this.

I have... now lemme go find the 1 file change and I'll post it back.

UPDATED:  K, found it.

On the apt-cacher server machine itself create the file:
```
/etc/apt/apt.conf.d/01proxy
```
In it put 1 line:
```
Acquire::http::Proxy "http://localhost:3142";
```

This causes the server machine's apt to go to apt-cacher and ask for the package, if not there it gets it and caches it so the 1st machine on the LAN that asks for the package will find it already there.

BTW, Instead of modifying ANY source.lists you can use this on the clients also.  Put the same named file in the same place on the client but with the contents of:
```
Acquire::http::Proxy "http://192.168.urapt.cacherip:3142";
```
You can then leave the source lists as they were (stock).

---

