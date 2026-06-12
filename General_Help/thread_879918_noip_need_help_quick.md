---
title: "noip need help quick"
date: 2008-08-04
forum: General Help
---

### Post by dxlwebs on 2008-08-04
hey all i have signed up with noip com and i have the install file for linux and it said to install i must use a command make but i have looked at the readme and its useless and it does not tell you how to do it in ubuntu does any one know ?

---

### Post by perlluver on 2008-08-04
> **dxlwebs said:**
> hey all i have signed up with noip com and i have the install file for linux and it said to install i must use a command make but i have looked at the readme and its useless and it does not tell you how to do it in ubuntu does any one know ?

Make sure you are in the folder, where the make program is located, then run make.  Read How to install anything in Ubuntu, In my signature.

---

### Post by AdamWood on 2008-08-04
It sounds like you need to compile the software. You'll probably need the build-essential package for a start.

Download and unzip the files into a clean directory and the from a a terminal 'cd' to that directory. The following commands are probably what you need but there should be a README or INSTALL file there with more instructions
```
sudo apt-get install build-essential
./configure
make
sudo make install

```
Optionally leave off the last line if you want to test the files in place before installing them for system wide access.

---

### Post by dxlwebs on 2008-08-04
thanks alot i used the syntech thing to install it i just added it as a new install package worked like a charm

---

