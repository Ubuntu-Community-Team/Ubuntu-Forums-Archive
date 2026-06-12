---
title: "Finding packages by size?"
date: 2008-08-03
forum: General Help
---

### Post by kokaku on 2008-08-03
Is there a way to find the size of installed packages? I don't see a column for that in Synaptic Package Manager, but I'd like to find out which packages are taking up the most space so I can remove them if they're not needed any more.

thx
andy

---

### Post by quibbler on 2008-08-04
> **kokaku said:**
> Is there a way to find the size of installed packages? I don't see a column for that in Synaptic Package Manager, but I'd like to find out which packages are taking up the most space so I can remove them if they're not needed any more.

thx
andy
Go to /var/cache/apt/archives with Nautilus
view as list - sort by size.

Regards quibbler

---

### Post by Muflon on 2008-08-04
You could also try

```
 dpkg-query -W  -f='${Installed-Size} ${Package} ${Status}\n' '*'|grep 'install ok installed'|cut -d ' ' -f 1-2|sort -nr|head -100
```

This will list the top 100 space using packages.  Change the 100 at the end of the line to see more or less packages.

Muflon

---

