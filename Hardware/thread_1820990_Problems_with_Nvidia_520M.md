---
title: "Problems with Nvidia 520M"
date: 2011-08-08
forum: Hardware
---

### Post by glaasje on 2011-08-08
Hi! ;)

I have a new laptop running Ubuntu 11.04 with 2 graphics cards. :D
1 intel integrated (works perfect) and a Nvidia 250M (wont work :( )

When i install Nvidia's drivers (they are available on 'restricted drivers') they install nicely but when i reboot Unity says that my hardware does not support Unity. :cry:

When i uninstall the Nvidia driver Unity works again.
When i try to use Bumblebee (to switch from graphics card) Bumblebee fails with:
```
ivo@ivo-W150HNM-W170HN:~$ optirun glxgears
lspci: -s: Invalid slot number
lspci: -s: Invalid slot number
 * Stopping Bumblebee X server bumblebee                                 [fail] 
lspci: -s: Invalid slot number
sudo: /usr/local/bin/bumblebee-disablecard: command not found

```

Can someone help me?

---

### Post by d!ck-t on 2011-08-13
Same problem.

lspci returns that the nVidia card is on 1:0.0, and bumblebee-enablecard and bumblebee-disablecard work fine.

Have Asus N53SV-HDU02, i7-2630QM, 6GB DDR3-1333, nVidia GT540M with optimus.

---

### Post by d!ck-t on 2011-08-13
Also occurs with optirun64.

---

