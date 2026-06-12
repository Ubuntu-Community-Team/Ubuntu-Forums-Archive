---
title: "Google Earth Instal"
date: 2008-10-17
forum: General Help
---

### Post by gee100104 on 2008-10-17
Downloaded GoogleEarthLinux.bin cannot install , asks for launch application?

---

### Post by Ms_Angel_D on 2008-10-17
Take a look at this tutorial [http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/](http://tombuntu.com/index.php/2007/11/28/how-to-install-google-earth-in-ubuntu/)

---

### Post by jonian_g on 2008-10-17
Rename it to GoogleEarthLinux.sh or GoogleEarthLinux.run and doubleclick it to start inastallation.

---

### Post by oldos2er on 2008-10-17
> **gee100104 said:**
> Downloaded GoogleEarthLinux.bin cannot install , asks for launch application?

 Assuming the file is on your desktop, open a terminal and run these commands one at a time:

cd Desktop

chmod a+x GoogleEarthLinux.bin

sudo ./GoogleEarthLinux.bin

---

### Post by snova on 2008-10-17
There's a program to generate a standard Ubuntu package for you that might be easier to use. It's in the "googleearth-package" package and contains a shell script, "make-googleearth-package". It automatically downloads and builds the .deb. (You still have to install the generated package manually.)

---

