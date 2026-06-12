---
title: "How To Change Login Settings From Command Line"
date: 2008-10-19
forum: General Help
---

### Post by Precipitous on 2008-10-19
How can I turn off the automatic login option from a command line? I upgraded from Hardy to Intrepid and am now booting to a black screen instead of a desktop. I need to be able to try a few different login options, but I am unable to as that I am set to be logged on automatically...

---

### Post by Sam on 2008-10-19
```
gksudo gedit /etc/gdm/gdm.conf-custom
```

In the section "[daemon]" find and remove:
```

AutomaticLoginEnable=true
AutomaticLogin={USERNAME}
```

---

