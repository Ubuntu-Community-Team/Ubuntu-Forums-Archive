---
title: "Problem with upgrade to 9.04 and pysqlite2"
date: 2009-05-10
forum: Installation &amp; Upgrades
---

### Post by Tolstoy the Cat on 2009-05-10
I recently upgraded Ubuntu to 9.04. During installation, it hit some problems with pysqlite2, but on the whole the system seems to run fine. Now, when software updates are available, they sometimes fail to install. 

I just tried to reinstall Python through Synaptic. It failed, giving me the following error:
```

E: python-pysqlite2: subprocess post-installation script returned error exit status 1
E: python-pysqlite2-dbg: dependency problems - leaving unconfigured

```
I'll be grateful of any help in fixing this.

Many thanks,
Tolstoy

---

### Post by imgabe on 2009-05-16
Hi,

I've been having the same problem lately. It looks like there is a compatibility issue between python 2.6 on ubuntu and pysqlite2. I fixed it by changing the default python interpreter for ubuntu back to python 2.5 by following the directions here:

[http://tareqalam.wordpress.com/2008/11/28/change-the-default-python-version-in-ubuntu/](http://tareqalam.wordpress.com/2008/11/28/change-the-default-python-version-in-ubuntu/)

(Note those directions are for going from 2.5 back to 2.4, so change the version number as appropriate)

If you have other programs that depend on python 2.6, they may not work after doing this though. Hopefully there will be an update to pysqlite soon, or there is a better fix out there.

---

