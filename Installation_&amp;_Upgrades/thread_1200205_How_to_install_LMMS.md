---
title: "How to install LMMS"
date: 2009-06-29
forum: Installation &amp; Upgrades
---

### Post by JoeyF on 2009-06-29
I downloaded the package, Ran it, Went to the program list, 
I opened the installer, Go to the program list, But when i open it it says:
"Error stating file '/usr/bin/lmms': No such file or directory"
How can i get it to work?
Thanks.
I am using 8.10

---

### Post by neu2buntu on 2009-07-06
are you trying to install from source or through synaptic, if from source you need to run these commands (1 at a time) inside the "lmms" directory through the terminal

```
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=/usr
make
sudo make install
```

i can walk you through this if unsure how to do this.......

---

