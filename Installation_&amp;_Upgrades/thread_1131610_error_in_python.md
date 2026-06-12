---
title: "error in python"
date: 2009-04-21
forum: Installation &amp; Upgrades
---

### Post by pancham on 2009-04-21
since 2 days I am not able to update regularly through update manager in ubuntu 9.04,,,, I am getting this message in details of the problem..

Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: parse error, in the '/var/lib/dpkg/available' near line 1:
 field name '/usr/lib/python-support/python-gconf/python2.5/gtk-2.0/gconf.so' must be fallowed by colon
dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
  field name '/usr/lib/python-support/python-gconf/python2.5/gtk-2.0/gconf.so' must be fallowed by colon
E: Sub-process /usr/bin/dpkg returned an error code (2)
package failed to install. Trying to recover:
 dpkg: parse error, in file '/var/lib/dpkg/available' near line 1:
  field name '/usr/lib/python-support/python-gconf/python2.5/gtk-2.0/gconf.so' must be fallowed by colon

---

### Post by Partyboi2 on 2009-04-21
Open a terminal  and try
```
sudo dpkg --clear-avail && sudo apt-get update
```

---

