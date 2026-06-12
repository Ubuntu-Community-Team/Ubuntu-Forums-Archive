---
title: "Error in Synaptic package manager"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by g160689 on 2009-08-06
(ubuntu 9.04)error message shows:
[LIST]
[*]Encountered a section with no package :header
[*]Problem with merge list /var/lib/dpkg/status
[*]The package list or status could not be parsed or opened
[*]_cache->open() failed, please report
[/LIST]i m unable to install any package, please help! thx..

---

### Post by drs305 on 2009-08-06
The first step is try to use the 'backup' status file to see if the problem still exists:
```

sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status

```

---

### Post by g160689 on 2009-08-06
it still exists........plz help me in details.thx

---

### Post by Soul-Sing on 2009-08-06
```
gksudo gedit /var/lib/dpkg/status
```
```
gksudo gedit /var/lib/dpkg/info
```

I believe you can search for "broken" packages.

---

