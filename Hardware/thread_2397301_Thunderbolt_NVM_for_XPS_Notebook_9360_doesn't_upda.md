---
title: "Thunderbolt NVM for XPS Notebook 9360 doesn't update"
date: 2018-07-27
forum: Hardware
---

### Post by jonasmarx on 2018-07-27
I can't get thunderbolt NVM for XPS updated.

I already tried:
```
sudo apt dist-upgrade
sudo service fwupd restart
fwupdmgr refresh
fwupdmgr update
```

```
sudo fwupdmgr get-updates *deviceid*
sudo fwupdmgr install *localfilenametocab*
```

Nothing of that worked. However it could even be that there are no updates and just Software wrongly proposes them to me.

---

