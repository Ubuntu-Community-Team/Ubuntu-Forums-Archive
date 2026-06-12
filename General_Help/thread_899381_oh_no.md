---
title: "oh no"
date: 2008-08-24
forum: General Help
---

### Post by Snappo on 2008-08-24
While installing awn window manager something went wrong, now i get this when i try to use the package manager.


A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'echo' is not known on line 57 in source list /etc/apt/sources.list, E:The list of sources could not be read.'

---

### Post by Nepherte on 2008-08-24
What's on line 57 in /etc/apt/sources.list? Post the output of:
```
cat /etc/apt/sources.list
```

---

### Post by nbayiha on 2008-08-24
just edit your sources.list 
do this 
```
 gksudo gedit /etc/apt/sources.list 
```
go to the line 57 and edit or remove it . I think you should have there and 'echo' written on this line which shouldn't be. Anyway can you past all you sources.list here. So we will figure out where is the problem.

---

### Post by Snappo on 2008-08-24
echo 'deb-src [http://ppa.launchpad.net/reacocard-awn/ubuntu](http://ppa.launchpad.net/reacocard-awn/ubuntu) gutsy main'  |  sudo tee -a /etc/apt/sources.list

removed

err still having problems

solved thanks

---

### Post by pauper on 2008-08-24
Change to:

> deb-src [noparse]http://ppa.launchpad.net/reacocard-awn/ubuntu[/noparse] gutsy main

---

