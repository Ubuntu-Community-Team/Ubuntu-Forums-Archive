---
title: "No compiler to install a python program."
date: 2008-10-14
forum: General Help
---

### Post by GregoryMA on 2008-10-14
I am trying to install a python program.  I don't seem to have anything to compile it though.  What compiler should I use?

gregory@gregory-laptop:~/drobilla-lad$ ./waf configure
Checking for program gcc                                : ok /usr/bin/gcc 
Checking for compiler version                           : ok 4.2.3 
Checking for program cpp                                : ok /usr/bin/cpp 
Checking for program ar                                 : ok /usr/bin/ar 
Checking for program ranlib                             : ok /usr/bin/ranlib 
Checking for compiler could create programs             : not found 
no programs

---

### Post by sumguy231 on 2008-10-14
I don't know much about Python myself, but I'm pretty sure it's usually interpreted rather than compiled. Does the program not come with installation instructions?

---

### Post by GregoryMA on 2008-10-15
I was missing a dependency but not a compiler.

[http://dev.drobilla.net/wiki/IngenInstallation](http://dev.drobilla.net/wiki/IngenInstallation)

---

