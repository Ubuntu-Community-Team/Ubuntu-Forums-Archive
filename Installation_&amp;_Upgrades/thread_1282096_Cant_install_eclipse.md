---
title: "Cant install eclipse"
date: 2009-10-03
forum: Installation &amp; Upgrades
---

### Post by noveus on 2009-10-03
Tried installing eclipse on my Ubuntu and failed. Here are the details.

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 91, in _process_transaction
    self.install_packages(**self.trans.kwargs)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 155, in install_packages
    self._mark_packages_for_installation(package_names)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 197, in _mark_packages_for_installation
    pkg.markInstall()
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 1076, in markInstall
    fixer.Resolve(True)
SystemError: E:Unable to correct problems, you have held broken packages.

---

### Post by stlsaint on 2009-10-04
you have broken packages in your system...try these couple steps...
1) run in terminal
```
sudo apt-get autoclean
```
2) go into synaptic package manager go to the Edit tab and select Fix Broken packaes.
3) restart and boot into recovery mode and select to Fix broken packages.

 4) after that run in terminal
```
sudo apt-get update && sudo apt-get dist-upgrade
```
 then try and install your app again...if still not working post here again for more help.

---

### Post by noveus on 2009-10-04
Okie ill try. Thanks

---

