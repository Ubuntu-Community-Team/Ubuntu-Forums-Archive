---
title: "Help! No Video!"
date: 2008-09-07
forum: General Help
---

### Post by solarwind on 2008-09-07
I accedentally installed the ati drivers from the ati website over the restricted drivers from the repository. Now everything's messed up! How do I reset everything back to the way it was with the normal restricted drivers?

---

### Post by darco on 2008-09-08
I did a quick search and found this....
[http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+drivers](http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+drivers)

this may work too...
sudo nano xorg.conf
look for the "driver" line and change to vesa
Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

reboot and you should be able to get back to the desktop...then install drivers via ENVY

good luck 
darco

---

### Post by solarwind on 2008-09-08
> **darco said:**
> I did a quick search and found this....
[http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+drivers](http://ubuntuforums.org/showthread.php?t=766699&highlight=ati+drivers)

this may work too...
sudo nano xorg.conf
look for the "driver" line and change to vesa
Section "Device"
        Identifier      "ATI Technologies Inc RV280 [Radeon 9200 PRO]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

reboot and you should be able to get back to the desktop...then install drivers via ENVY

good luck 
darco

What is ENVY?

---

### Post by darco on 2008-09-08
[http://ubuntuforums.org/showthread.php?t=515573&highlight=envy](http://ubuntuforums.org/showthread.php?t=515573&highlight=envy)

the thread looks old..you can install envy via synaptic....

darco

---

### Post by solarwind on 2008-09-08
> **darco said:**
> [http://ubuntuforums.org/showthread.php?t=515573&highlight=envy](http://ubuntuforums.org/showthread.php?t=515573&highlight=envy)

the thread looks old..you can install envy via synaptic....

darco

Thank you! Problem solved!

---

