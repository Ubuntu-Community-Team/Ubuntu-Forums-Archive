---
title: "Can't install HP Printer using hplip"
date: 2016-09-25
forum: Hardware
---

### Post by tonma on 2016-09-25
Hello,

I downloaded hplip-3.16.9.run from [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html), and when I click the run, it starts installing, but at the end I get this error message:

**The file you opened has some invalid characters.**


What is it?

*Edit: I've ended up doing hp-setup -i in terminal and it installed (though an older version)

Ty!

---

### Post by kc1di on 2016-09-25
what version of ubuntu are you running?
3.16.3 is in the 16.04 repositories. and installs fine with the software center.  
I also recommend you install synaptic package manager.
You can also install the printer from CUPS by going to any browser and typing the following in the address bar.
```
http://localhost:631
```
then follow the instruction on screen.

Which printer are you trying to install?
Good luck

---

