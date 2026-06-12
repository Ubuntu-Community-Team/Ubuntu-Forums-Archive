---
title: "/etc/apt/preferences - how to ignore php"
date: 2008-09-27
forum: General Help
---

### Post by SDE on 2008-09-27
I made a custom build of PHP and I would like to make sure it can't be accidentally installed over by **apt-get install php5**

There's a few things i'd like to do this for, but I'm wondering exactly how I should setup my /ec/apt/preferences for this.

```
     Package: <package>
     Pin: <pin definition>
     Pin-Priority: <pin's priority>

```

how would i use that format to ignore everything php? I think I can make the package name ***php***, and the Pin-Priority **-1** , but I'm not sure what the Pin would be.

Any help would be greatly appreciated.

Thanks

---

