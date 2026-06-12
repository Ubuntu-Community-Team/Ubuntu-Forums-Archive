---
title: "Powersave failed to unload"
date: 2006-06-02
forum: Hardware &amp; Laptops
---

### Post by awakatanka on 2006-06-02
I have the following error if i try to suspend to disk/ram with my laptop if i use powersave.

**suspend2ram failed on unloading 'rt2500'. Trying to recover...**

After a search i found this german site that say that you have to add 
[B]
UNLOAD_MODULES_BEFORE_SUSPEND2DISK= [/B]

at the file **/etc/sysconfig/powersave**

Now this is a solution for the novell powersave but this file isn't in kubuntu dapper. 

What to do to get it to work. Removing pcmcia card with hand is no solution because it has to go automatick.

source : [http://www.linux-club.de/ftopic59809.html](http://www.linux-club.de/ftopic59809.html)

---

