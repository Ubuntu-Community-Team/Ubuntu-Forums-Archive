---
title: "[SOLVED] Removing unused configuration files and folders"
date: 2008-08-04
forum: General Help
---

### Post by MidnightJulia on 2008-08-04
Hi! 

I've found that in my quest for the perfect Ubuntu system some programs that I've installed and then removed again (of course with apt-get install  / remove) have left some configuration files. Now I could delete these by hand but is there a smarter way of solving this? 

/MJ

---

### Post by cszikszoy on 2008-08-04
using apt-get remove --purge <package> is supposed to remove all configuration files.

**edit, there's also lots of information here: [http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/](http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/)

---

### Post by brian_p on 2008-08-04
> **MidnightJulia said:**
> Hi! 

I've found that in my quest for the perfect Ubuntu system some programs that I've installed and then removed again (of course with apt-get install  / remove) have left some configuration files. Now I could delete these by hand but is there a smarter way of solving this? 

/MJ

The --purge option to apt-get removes system configuration files. Those in $HOME you do by hand.

---

### Post by MidnightJulia on 2008-08-04
Wow. I find it strange that --purge isn't a the default value.

Thank you both! I'll think about this next time I remove a package :)

---

