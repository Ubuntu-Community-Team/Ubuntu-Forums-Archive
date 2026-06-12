---
title: "Gnu-mp"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by vivekvachhani on 2009-04-02
Hiii
   I want to install GNU-MP library(4.2.4) in mu UBUNTU..But when i gave the command ./CONFIGURE it wasnt successfully installed.. PLEASE HELP ME. . .

---

### Post by Partyboi2 on 2009-04-02
I think gnu-mp is in the ubuntu repos as libgmp3c2. You can open up Synaptic and search for it and install which is easier then trying to compile something from source.


Running ./configure does not install a program, you will need to run ```
make
``` which builds the program then finally install it with ```
sudo make install
```


[B]
[/B]

---

