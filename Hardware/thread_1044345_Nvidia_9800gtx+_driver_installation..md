---
title: "Nvidia 9800gtx+ driver installation."
date: 2009-01-19
forum: Hardware
---

### Post by gtsorensen on 2009-01-19
Hello I just installed Ubuntu last night and for the life of me i cannot get these nivida drivers to install.  Please assume i know nothing about ubuntu when telling me what to do, because i really know nothing.  Ok so last night i downloaded the driver "Nvidia-Linux-x86-173.08-pkg1.run"
I read the guide for installing it and it said to type "sh NVIDIA-Linux-x86-173.08-pkg1.run" to install it.  I'm assuming i type this into the terminal correct?  Ok if correct i type that into the terminal and it says i cannot run it.
my system also does not recognize any restricted drivers for my card in the the system-admin-restricted drivers because there simply is not a restricted drivers option.
thanks for any help at all guys.

---

### Post by Zeroberry on 2009-01-19
Posted the same thread twice. Check other for suggestion.

---

### Post by jocko on 2009-01-19
> **gtsorensen said:**
> ...
my system also does not recognize any restricted drivers for my card in the the system-admin-restricted drivers because there simply is not a restricted drivers option.
...
Exactly what do you mean with "there simply is not a restricted drivers option"?
Do you mean you can't find the restricted drivers manager? It's in System --> Administration --> Hardware drivers. Or you can start it from a terminal with the command:```
gksudo jockey-gtk
```
Try to get the driver through the restricted drivers manager before you resort to installing with nvidia's installer (and if you really have to use nvidia's installer, why not use the newest driver, 180.22 released just a little bit more than a week ago, instead of that old one from last april you downloaded?).

---

