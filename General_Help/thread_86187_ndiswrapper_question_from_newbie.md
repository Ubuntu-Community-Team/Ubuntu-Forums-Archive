---
title: "ndiswrapper question from newbie"
date: 2005-11-04
forum: General Help
---

### Post by RockKing on 2005-11-04
I got my wireless card to work in Ubuntu by using ndiswrapper. However, every time I boot up, I have to use 'sudo modprobe ndiswrapper' in order for the wireless card to be recognized. Is there a way I can setup Ubuntu to automatically setup ndiswrapper so I don't have to enter the command every time I want to use it? Thanks.

---

### Post by Lambert on 2005-11-04
```
sudo ndiswrapper -m
```

Use this command after modprobe ndiswrapper and it will write a config file to initiate at startup.

---

### Post by acascianelli on 2005-11-04
Also, you can add 'ndiswrapper' to /etc/modules.  Heres mine for reference

```

acascianelli@ubuntu:~$ more /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
**ndiswrapper**
acascianelli@ubuntu:~$
```

---

### Post by RockKing on 2005-11-04
Excellent. Thanks for the help guys. Much appreciated.

---

