---
title: "Firefox Offline"
date: 2008-08-03
forum: General Help
---

### Post by kf4tqj on 2008-08-03
With Ubuntu 8.04 Firefox 3.0 always opens in Offline Mode. How do I change that?
Thanks,
Woody / KF4TQJ

---

### Post by coffeecat on 2008-08-03
[This link]("http://kb.mozillazine.org/Toolkit.networkmanager.disable") might be the answer. Found from a search in [Firefox Support Forum]("http://support.mozilla.com/en-US/kb/Support+Website+Forums")

---

### Post by Tom--d on 2008-08-03
If you are not using Network Manager to get a connection. Firefox will start in Offline Mode.
This is normal.
All you need to do if remove Network Manager.

```
sudo apt-get remove network-manager
```

Done :)
No more offline mode.

---

### Post by Seinfeld on 2008-12-12
> **Tom--d said:**
> If you are not using Network Manager to get a connection. Firefox will start in Offline Mode.
This is normal.
All you need to do if remove Network Manager.

```
sudo apt-get remove network-manager
```

Done :)
No more offline mode.

Perfect.. Thanks a lot.. I am using Speedtouch USB modem so that is why I had the problem.. Fixed now.. Thanks million....

---

### Post by Kar.ma on 2009-02-14
If someone doesn't want to remove Network Manager, there is a simple solution, that is avoiding firefox connecting to Network Manager for retreiving info over internet connection.

Simply type in Firefox address field:
```
about:config
```
and set
```
toolkit.networkmanager.disable
```
to true.

You only need a 3.0.2 or higher release of Firefox.

---

### Post by fakhri on 2010-07-04
bravo brother. It worked for me. :)

---

