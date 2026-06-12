---
title: "Error occured while update ubuntu 8.10"
date: 2009-03-08
forum: Installation &amp; Upgrades
---

### Post by tusherr on 2009-03-08
Update icon show a red icon and a error message like this

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E: Problem parsing dependency Pre-Depends, 
E: Error occurred while processing libgl1-mesa-glx (NewVersion1), 
E: Problem with MergeList /var/lib/dpkg/status, 
E: The package lists or status file could not be parsed or opened.'

What should I do

---

### Post by Partyboi2 on 2009-03-08
Open a terminal (Applications>Accessories>Terminal) and change the status file over.
```
cd /var/lib/dpkg
mv status status-bad
cp status-old status
```

---

