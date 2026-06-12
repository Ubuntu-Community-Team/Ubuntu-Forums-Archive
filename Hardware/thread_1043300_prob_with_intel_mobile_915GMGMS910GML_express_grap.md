---
title: "prob with intel mobile 915GM/GMS/910GML express graphics"
date: 2009-01-18
forum: Hardware
---

### Post by khalilmax on 2009-01-18
hello 
i can t install the driver "intel mobile 915GM/GMS/910GML express graphics" 
i have kubuntu 8.10 using the VESA driver I tried several tuto.  

"glxinfo | grep" direct rendering "replied yes but compiz does 

and I've seen that compiz doesnt work with "vesa"  [http://forlong.blogage.de/entries/pages/Compiz-Check](http://forlong.blogage.de/entries/pages/Compiz-Check) 
plsssss help me

---

### Post by densou on 2009-01-20
Compiz + Intel = ](*,) :frown:

Paste here your xorg.conf ;)

You must add these repositories for getting new Intel video drivers:
```
deb http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/intel-gfx-testing/ppa/ubuntu intrepid main
```

---

