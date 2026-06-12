---
title: "Fixed: Firefox hangs after upgrade from 8.04 to 8.10"
date: 2009-02-02
forum: Installation &amp; Upgrades
---

### Post by ewanchic on 2009-02-02
If you upgrade your machine from Ubuntu 8.04 to Ubuntu 8.10, and notice that Firefox is hanging/freezing/acting very slow yet your system processes aren't being used at all...not really, 

and

You updated your flash plug-in to adobe's flash 10, 64-bit from adobe's site...then this is the fix for you. 


Step 1: Un-install adobe's flash 10 package
```
user@host:~# sudo dpkg -r adobe-flashplugin
```

Step 2: Install Ubuntu's non-free-flash plug-in
```
user@host:~# sudo apt-get install flashplugin-nonfree
```

All done. No reboots should be necessary. If this helped you out in anyway, give me a shout. Thanks (^_^)

Eric

---

