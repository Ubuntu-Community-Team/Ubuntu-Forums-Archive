---
title: "&quot; Error : screen not found &quot;"
date: 2005-04-12
forum: Hardware &amp; Laptops
---

### Post by Flying_Vortex on 2005-04-12
Ok before we go any further i must let you all know that i have never actaully used any sort of Linux ;-) , but one has to start somewhere   :smile: 

OK well basically when it asks me to login that is all fine.. But when im half typing my password a message appears regarding XServer or something similar and telling me its not working

When that screen goes away ( I can select Yes to see the problem or no for it to go away ) I type in my Password and then im in

Then i type in " startx " to log into the KMD and i get the message " Error: screen not found " which i believe is something to do with the Xserver

Anyone come across this problem before? Any help is appreicated, Thanks

PC Specs:

AMD 64 3000+ 939
Gigabyte K8N9-F
1gb Pc3200 Ram ( Adata )
200gb Sata Hard Drive, Seagate
Nvidia Geforce 6600gt
Dell 17inch Monitor CRT Screen

If you need any other info please let me know. Ty

---

### Post by kuleali on 2005-04-12
Try

sudo dpkg-reconfigure xserver-xfree86

---

### Post by Flying_Vortex on 2005-04-12
Gives me the error

Package 'xserver' is not installed

And then it basically tells me keys to press to get info on it

Any ideas?

---

### Post by kuleali on 2005-04-13
Try:
sudo apt-get install ubuntu-base
sudo apt-get install ubuntu-desktop

Are you using warty or hoary ?

---

