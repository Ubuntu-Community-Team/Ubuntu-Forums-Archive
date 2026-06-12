---
title: "update manager broke"
date: 2009-05-05
forum: Installation &amp; Upgrades
---

### Post by raiwo on 2009-05-05
installed latest updates, something went wrong & update-manager update didn't install correctly: getting following error:

```
sudo update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 33, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 74, in <module>
    from Core.MyCache import MyCache, NotEnoughFreeSpaceError
  File "/usr/lib/python2.6/dist-packages/UpdateManager/Core/MyCache.py", line 32, in <module>
    import DistUpgrade.DistUpgradeCache
  File "/usr/lib/python2.6/dist-packages/DistUpgrade/DistUpgradeCache.py", line 64, in <module>
    self.dir = dir

```
[launchpad report]("https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/372126")

tried to reinstall update-manager tru synaptics but it did not help, anuone got any solutions for this one?

---

### Post by raiwo on 2009-05-05
found solution: had to reinstall update-manager-core

---

