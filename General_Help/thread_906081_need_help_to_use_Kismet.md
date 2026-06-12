---
title: "need help to use Kismet"
date: 2008-08-31
forum: General Help
---

### Post by luxubuabac on 2008-08-31
i just installed and tried to run Kismet. Unfortunately i got some probs and cannot run Kismet so far ...
when i tried to follow the instructions how to run Kismet .. the errors are:
Unable to find libncurses or libcurses 

i tried to install libncurses by : sudo apt-get install libncurses5
but everything ... is still same .. Kismet cannot run

Please help me out:confused::confused::confused:

---

### Post by MoLE on 2008-08-31
for kismet to function properly under ubuntu the default setup requires root access.

thus:
```
sudo kismet
```

and enter your user password when prompted.

---

