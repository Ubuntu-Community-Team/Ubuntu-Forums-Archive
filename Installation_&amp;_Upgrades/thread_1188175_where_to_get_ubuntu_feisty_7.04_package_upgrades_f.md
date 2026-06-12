---
title: "where to get ubuntu feisty 7.04 package upgrades from?"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by SSkret on 2009-06-15
When I run the package manager to install new packages on my ubuntu feisty 7.04 installation I get a bunch of 404 since feisty distributions do not exist any more. Could you please let me know how can I get these packages?
 
Thanks,
Swavek

---

### Post by zvacet on 2009-06-15
If you just started to use Ubuntu best thing will be to install new Ubuntu release Jaunty.I'm telling you this because Feisty is not supported anymore.If you still want to get updates for Feisty then you will lhave to edit your source list by typing in terminal

```
gksudo gedit /etc/apt/sources.list
```

and then replace all **archive.ubuntu.com** with **old-releases.ubuntu.com**

For example

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty main restricted

deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) feisty main restricted

I think installing new release is better idea.

---

### Post by SSkret on 2009-06-15
Thanks, it worked fine.
 
Swavek

---

