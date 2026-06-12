---
title: "HOW-TO : Install/Fix HP Printer"
date: 2010-01-01
forum: Hardware
---

### Post by mikemikemike on 2010-01-01
Originally this was written up for a HP1020. However I decided to try it with my 710c, I changed one or two things. It should work for most HP Printers.


In Terminal: Copy and Paste [SIZE=1](right click in Terminal or Ctrl+Shift+V)[/SIZE] Each step one at a time make sure it is done before pasting the next command.

Step 1
```
sudo apt-get install build-essential
```Step 2
```
wget -O foo2zjs.tar.gz http://foo2zjs.rkkda.com/foo2zjs.tar.gz
```Step 3
```
tar zxf foo2zjs.tar.gz
``` Step 4
```
cd foo2zjs
``` Step 5
```
sudo make uninstall
``` Step 6
```
make
``` Step 7
```
./getweb 1020
``` Step 8
```
sudo make install install-hotplug cups
``` Step 9
```
sudo make cups
```

---

