---
title: "Python install"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by clinquist on 2009-03-18
I am new to Linux.  I always used DOS and Windows before.  Now I'm making the switch, but I have a problem:  I have a program written in Python ("setup.py") on a USB drive.  I can go into the file browser and see the files.  
I go to the Synaptic package manager and can't figure out what to do.

I'm told that I need to run  

"Python setup.py install"  to run the package.  I don't have a clue.  What should I do?

---

### Post by taurus on 2009-03-18
Assuming your USB thumbdrive is mounted to /media/disk, open a terminal and do

Applications -> Accessories -> Terminal
```
cd /media/disk
python setup.py install
-or-
sudo python setup.py install 
(If you need root privilege.)
```

---

### Post by clinquist on 2009-03-18
That worked!

Thanks!

---

