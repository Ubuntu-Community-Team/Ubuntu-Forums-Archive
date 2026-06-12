---
title: "Moblock?"
date: 2008-10-18
forum: General Help
---

### Post by eightbitpotion on 2008-10-18
So I'm natively running linux again for the first time in like 5 years... stuff has changed a lot.  Anyway, my question...  

Moblock's setting are much different than Peerguardian's....  I generally block "government" and "anti-p2p", so what settings would equal this?  Any thoughts on this?

---

### Post by jre on 2008-10-19
Have a look at /usr/share/doc/moblock-control/README.blocklists.gz, there you will find much information.
PeerGuardian uses the blocklist by bluetack.co.uk. The government list has been removed more than a year ago. AFAIK its contents are in the "anti-p2p" list now.

So what you want is:
[http://www.bluetack.co.uk/config/level1.gz](http://www.bluetack.co.uk/config/level1.gz)

Further some/most of the list maintainers have left bluetack and make their own lists now. You will find their equivalent to level1 here:
[http://blocklist1.snowmanuk.net/Lists/PrimaryThreats.zip](http://blocklist1.snowmanuk.net/Lists/PrimaryThreats.zip)

Note that this link is only valid until november.

---

