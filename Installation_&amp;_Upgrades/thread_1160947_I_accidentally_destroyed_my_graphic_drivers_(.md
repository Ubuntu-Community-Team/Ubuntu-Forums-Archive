---
title: "I accidentally destroyed my graphic drivers :("
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by BramWillemsen on 2009-05-16
Hello,

Today i gathered some courage and tried to manually install the radeonhd drivers since the normal radeon drivers were giving me some trouble. (fglrx isnt supported anymore for ati x1950 in jaunty). To this end i used the guide positioned at [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD). I first deinstalled the xorg radeon drivers.  Everything seemed to be okay up till the diagnostic commands. I got the "software rasterizing" output when i did 'glxinfo | grep "renderer string"' , apperantly something was wrong. 

I never installed something outside of synaptic before. Therefore i do not know how to remove the things i just installed. I did 'make uninstall' within the DRM directory that was created. within a flash the processing was done which gave me the impression that not that much happened. I couldnt find a directory to 'make uninstall' the radeonhd drivers so i never did.

Everything was laggy and such because my drivers were obviously still broken. I tried to reinstall the xorg radeon drivers in order to get back to my previous state. After reinstalling the packages that i deleted and rebooting i found out that my drivers are still broken.

Right now everything that is related to graphics is really laggy. The desktop effects are disabled too. Could anyone give me a tip about how to fix this? I'm really unable to figure out myself what to do now since i dont know how to clean up the things i installed with [https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD). Please save me ;)

Bram

---

### Post by BramWillemsen on 2009-05-16
i'm still not closer to the solution. please help me. The only thing i can think of is a reinstall, but this should be really trivial

---

### Post by BramWillemsen on 2009-05-16
bump

---

### Post by BramWillemsen on 2009-05-17
i tried uninstalling the things i installed and then reinstalling the xorg radeon package. Still nothing happening. Please help

---

### Post by briandu on 2009-05-17
Are u stating you cannot get a graphic display at all only command line?

What version Ubuntu are u using?

Do you still have access to the internet?

---

### Post by briandu on 2009-05-17
You do realise you can change screen to boot up a view graphics as standard VGA and then recover?

The situation is not that bad and can be recoverd on the command line

---

### Post by BramWillemsen on 2009-05-17
Hello,

After a loooong trial and error session it finally seems to work again. I am using the xorg radeon package again. Installing the xorg radeonhd version instead (through synaptic this time) gives me a 640x480 display and no 3d acceleration. 

i guess i'll just keep on using the xorg radeon package. I still dont know what went wrong (and why i cant install radeonhd) but at least i got some desktop effects back.

---

