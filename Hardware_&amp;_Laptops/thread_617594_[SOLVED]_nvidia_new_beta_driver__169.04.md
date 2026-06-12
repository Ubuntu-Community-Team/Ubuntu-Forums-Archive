---
title: "[SOLVED] nvidia new beta driver  169.04"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by nicolasdiogo on 2007-11-19
hi folks,

i am trying to solve some problem i am having with a laptop asus a6tc's graphic card NVidia geforce go 7300.

the two drivers available in ubuntu repositories are not working well thus i am testing the new beta driver 169.04

[http://www.nvidia.com/object/linux_display_ia32_169.04.html](http://www.nvidia.com/object/linux_display_ia32_169.04.html)

it works like a charm.

But (and there is always a But).

every time that i reboot, i am forced to reinstall it.

i have used the NVidia installation method and i have previously installed other nvidia beta drivers.

i would really appreciate some assistance here.

many thanks

---

### Post by nicolasdiogo on 2007-11-20
i think i figure what the problem was.

i have amended:
/etc/default/linux-restricted-modules-common

and added module nv as below:

DISABLED_MODULES="nv "

---

### Post by tim71 on 2007-11-20
the presence of the file
```
/lib/linux-restricted-modules/.nvidia_new_installed
```
made this driver installation a no-go - anything else had no affect.

To be more precise - the presence of this file caused X startup to fail every time after the installation of this driver. I removed this file from there and everything worked... then put it back just for the test and it was "broken" again.

Interesting thing is, that this issue was never a problem with previous driver versions - maybe it will be fixed in next release...

---

