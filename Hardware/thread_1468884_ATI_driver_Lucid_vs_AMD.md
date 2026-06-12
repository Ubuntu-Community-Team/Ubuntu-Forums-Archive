---
title: "ATI driver: Lucid vs AMD"
date: 2010-05-01
forum: Hardware
---

### Post by Sanhime on 2010-05-01
Does Ubuntu (Lucid) grab their ATI drivers directly from the AMD site when you use the Hardware Drivers detection?  Should I just grab the latest drivers from ATI/AMD or use the driver in the Hardware Driver detect?

---

### Post by urbanus on 2010-05-01
The ATI driver in the repository is added by someone in the ubuntu tech community, and only after it has passed some tests. So it's usually an older version than the latest one on the ATI web site.

What you can do is use the installer from the ATI web site to create DEB files/packages that you then can install, and uninstall if they don't work that well. You can also have the installer install itself directly, but removing it is probably a lot more painful then.

There are guides on how to create packages from the installer and how to use them. Trying them out shouldn't be a big problem since you can remove them from the package manager :)

Does that answer your question?

---

### Post by Yellow Pasque on 2010-05-01
Lucid got a special pre-release of Catalyst, so ATI/AMD used the version in Lucid to create their current Catalyst. [http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ](http://www.phoronix.com/scan.php?page=news_item&px=ODE0MQ)
Basically, I would recommend using the version of Catalyst that ships with Lucid at this point in time (that may change in a couple months).

EDIT: This might also interest you if you have a delay when maximizing windows: [http://www.phoronix.com/forums/showthread.php?t=21846](http://www.phoronix.com/forums/showthread.php?t=21846)

---

