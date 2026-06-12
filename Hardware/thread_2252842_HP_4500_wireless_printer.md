---
title: "HP 4500 wireless printer"
date: 2014-11-15
forum: Hardware
---

### Post by ilse2 on 2014-11-15
Hi!

I am having troubles installing my HP 4500 wireless printer.
I already installed cups with the command: sudo apt-get install cups
After that I downloaded the hplip-3.14.10 file and tried to install it by using this commands in terminal:
cd Desktpo and sh hplip-3.14.10.run
After this I always get an error: A required dependency cups is still missing, cannot continue without dependency.

Hopefully someone can help me out.. Im using ubuntu 12.04 lts

Thanks

---

### Post by kc1di on 2014-11-15
Hello ilse2 and Welcome to Ubuntu,

What version of ubuntu are  you using?

hplip 3.14 is in the repository it should work with hp4500.  

you might want to install hplip-gui and use that it will install the printer for you. You can do that in a terminal by typing:
```
sudo apt-get update
sudo apt-get install hplip-gui
```

then look for hplip-toolbox.

Have you tried the printer tool in the System Setting panel also?  It usually will find your printer and install it for you also.

---

