---
title: "[SOLVED] Make WIndows master boot option?"
date: 2008-09-26
forum: General Help
---

### Post by Fc1032 on 2008-09-26
Hi All,

Sorry if this question has been asked before... I couldn't find anything similar to this... :( Anyway, here is what happened...

Installed Ubuntu onto my main computer so it can dual boot with windows vista. I really want ubuntu alone, but my parents have bad adaptability, so i have to have the windows options.

After successfully installing Ubuntu, everything works fine but when i turn the computer on, the boot options automatically loads ubuntu after x seconds instead of windows. Windows is an option though, its just that it has to be selected

Can someone please tell me how to make GRUB load load windows after x seconds instead of ubuntu? 



Many thanks! 

P.S I now have Ubuntu on all computers!!! (well Xubuntu on one...)

---

### Post by drs305 on 2008-09-26
The easiest and safest way is to install StartUp-Manager. Then start it up and on the main tab set the Default OS setting to windows. For more info, look at the link in my signature line. There are lots of tweaks you can make with SUM.

To install:
```
sudo apt-get install startupmanager
```

To run:
System, Administration, StartUp-Manager

---

### Post by Fc1032 on 2008-09-26
[EDIT: hello again, i found the 'startup manager' on the programs list] 

thanks again!

---

