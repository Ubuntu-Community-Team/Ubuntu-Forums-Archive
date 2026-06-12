---
title: "[SOLVED] Will upgrading destroy my XP partition?"
date: 2008-12-25
forum: Installation &amp; Upgrades
---

### Post by Cuttysark on 2008-12-25
How can I upgrade from 8.04 to 8.10 without screwing up my XP partition?

---

### Post by Partyboi2 on 2008-12-25
You can do a network upgrade or use the alternate cd to upgrade. 
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by Cuttysark on 2008-12-25
I just tried the network upgrade but it says I need to do any updates first and unfortunately I have a problem with that. For about three weeks now, I've been getting a message telling me it can only do a partial update, then when it's done, it tells me it can't authenticate the following brasero, libbabl-0.0-0 and libgegl-0.0-0. The thing is, it isn't even doing the partial cause the same list of available updates always shows at the beginning, some of them security updates. Barsero disappeared from the list for a few days but it's back now?

---

### Post by upchucky on 2008-12-25
click system>administration>software sources

set to main and if that does not get all sources there are other sources listed there to try also

---

### Post by cariboo on 2008-12-25
IF you ever get a message syaing that it can only do a partial upgrade, don't do anything, give it a couple of days for the dependencies to show up. If you really have to do a partial upgrade, open a terminal and type:

```
sudo aptitude safe-upgrade
```

The above command will do an upgrade without breaking anything.

Jim

---

### Post by Cuttysark on 2008-12-26
Jim, thankyou for the advice, that did the trick perfectly. I had this problem for going on four weeks now and was starting to worry regarding the security updates not going through. Now I can go ahead upgrading to 8.10, well, once I know it will work with my nvidia graphics card that is.

---

