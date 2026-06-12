---
title: "Disable touchpad click"
date: 2007-02-10
forum: Hardware &amp; Laptops
---

### Post by aznewsh on 2007-02-10
I have Kubuntu 6.10 EDGY installed on an HP DV9040 Laptop, the installation works great, there are just a few things I am looking to refine, one in particular is disabling the the mouse click when you tap on the touchpad, note not the actual buttons just the tap on the pad click.

I have tried as I do with any other problem to search for a solution and am coming up empty
I will be happy to provide any more info that may be required.

I apologize if I selected the incorrect forum and have no problem with an admin moving this post to a more suitable one

Thanks in advance, Ubuntu rocks!

---

### Post by TheWizzard on 2007-02-10
use qsynaptics
see
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

you need to run 
```
qsynaptics -r
```
in order to restore your settings when you log in. you can put it in a script in the folder ~/.kde/Startup

---

