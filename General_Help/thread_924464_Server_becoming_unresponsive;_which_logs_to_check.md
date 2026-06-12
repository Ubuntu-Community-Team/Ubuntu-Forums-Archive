---
title: "Server becoming unresponsive; which logs to check?"
date: 2008-09-19
forum: General Help
---

### Post by antun on 2008-09-19
I have a headless Ubuntu server that I use as my home media/file system. It really doesn't get much traffic, and has two RAIDed HDs.

It's started becoming unresponsive. I can't access it either using SSH or with network browsing (DAV, right?). Oddly, it does seem to respond to pings. I can recover by power-cycling.

Any pointers as to which logs to check?

Thanks,

Antun

---

### Post by dabang on 2008-09-19
```
/var/log/messages
```

and of course any server log there...

or maybe

```
sudo grep -i error /var/log/*
```

will help you.

---

### Post by antun on 2008-09-20
Thanks; I guess I could have just grepped the log directory in the first place like you suggested. 

The only relevant-looking entries with error in them lookied like this:

> 
/var/log/evms-engine.5.log:Oct 10 16:40:18 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram9 failed with error code 22: In
valid argument
/var/log/evms-engine.log:Sep 19 21:30:57 vindaloo _5_ Engine: load_module_plugins: Loaded from /lib/evms/2.5.4/error-1.0.2.so.
/var/log/evms-engine.log:Sep 19 21:30:57 vindaloo _5_ Engine: load_module_plugins:   short name:  Error
/var/log/evms-engine.log:Sep 19 21:30:57 vindaloo _5_ Engine: load_module_plugins:   long name:   Error Device Manager
/var/log/evms-engine.log:Sep 19 21:30:58 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/hdc failed with error code 123: No m
edium found
/var/log/evms-engine.log:Sep 19 21:30:58 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/hdd failed with error code 123: No m
edium found
/var/log/evms-engine.log:Sep 19 21:30:58 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram0 failed with error code 22: Inva
lid argument
/var/log/evms-engine.log:Sep 19 21:30:58 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram1 failed with error code 22: Inva
lid argument
/var/log/evms-engine.log:Sep 19 21:30:58 vindaloo _3_ Engine: engine_open_object: Open of /dev/evms/.nodes/ram10 failed with error code 22: Inv
alid argument


The timestamps on those entries correspond with the last time the server became unresponsive. I looked up EVMS, and it seems to be used for RAID support. I set this box up with software RAID. Could that be what's going wrong here? One of the drives in the RAID array? I did the following, which I think tells me what's going on with the RAID array:

> 
# cat /proc/mdstat 
Personalities : [raid1] 
md1 : active raid1 hda2[0] hdb2[1]
      1927680 blocks [2/2] [UU]
      
md0 : active raid1 hdb1[1]
      310640768 blocks [2/1] [_U]


-Antun

---

### Post by antun on 2008-10-01
This turned out to be a failing hard disk. I wrote a blog post to summarize the process of checking and rebuilding a RAID array:

[http://www.antunkarlovac.com/blog/2008/09/30/restoring-a-broken-linux-raid-array/](http://www.antunkarlovac.com/blog/2008/09/30/restoring-a-broken-linux-raid-array/)

-Antun

---

