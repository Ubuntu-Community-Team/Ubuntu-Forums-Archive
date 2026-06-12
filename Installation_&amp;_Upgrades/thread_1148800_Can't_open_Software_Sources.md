---
title: "Can't open Software Sources"
date: 2009-05-04
forum: Installation &amp; Upgrades
---

### Post by matthewboh on 2009-05-04
I've had a lot of problems upgrading - I had to re-boot my machine during the middle of it because it had locked on update-passwd, but I've been able to restart it and using the command line, get it updated.

Now I'm having a problem with changing the Software Sources - I select System | Software Sources, it tries to start up the GUI, then just goes away.  Any ideas?

Also having problems with the display - grrr.

---

### Post by Partyboi2 on 2009-05-04
Try starting it from a terminal to see if it provides any more info on why it is closing
```
gksu software-properties-gtk
```

---

### Post by matthewboh on 2009-05-04
Gave that a try and got

```
gksu software-properties-gtk
Traceback (most recent call last):  File "/usr/bin/software-properties-gtk", line 44, in <module>
    from softwareproperties.gtk.SoftwarePropertiesGtk import SoftwarePropertiesGtk
ImportError: No module named softwareproperties.gtk.SoftwarePropertiesGtk

```

---

### Post by Partyboi2 on 2009-05-04
Try reinstalling the software-properties-gtk package
```
sudo apt-get --reinstall install software-properties-gtk
```

---

### Post by matthewboh on 2009-05-04
Gave that a shot and still having the same problem.

PS - Love Melbourne - I need to get myself back to Australia!

---

### Post by Partyboi2 on 2009-05-05
Try 
```
sudo dpkg-reconfigure python-software-properties
``` I also found a open bugreport, if you have any additional info that might help feel free to add it to the bugreport.
[https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/361180](https://bugs.launchpad.net/ubuntu/+source/software-properties/+bug/361180)

---

