---
title: "I have a printer it works, HPLIP can't detect it"
date: 2007-01-19
forum: Hardware &amp; Laptops
---

### Post by nu2this on 2007-01-19
I have installed an HP C3180, it works in every way, except one. When I try to use the HPLIP toolbox it says that my printer is not detected. So while I can print,copy,& scan I have no idea
about ink levels.  
I have put up a screenshot to show what I get after System>Preferences>HPLIP toolbox
Here's what I've done to date:
1) i clicked the CUPS web key set my printer as default
2)Opened Terminal```
sudo /etc/init.d/hplip restart
``` 
this is what I got
 * Stopping HP Linux Printing and Imaging System                         [ ok ] 
 * Starting HP Linux Printing and Imaging System                         [ ok ] 
Even after clicking refresh I get this. What do I need to do to get this to at least tell me ink levels?

---

### Post by Ranjit on 2007-01-19
Do a hp-setup.
Why dont ask me.:guitar:

---

