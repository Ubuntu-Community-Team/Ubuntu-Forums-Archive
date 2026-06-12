---
title: "Saitek p2500 Driver install."
date: 2011-05-05
forum: Hardware
---

### Post by CrimzonEyed on 2011-05-05
I tried to use my Saitek p2500. 
But i had some problem with the control, the d-pad wasn't working as it should so i figured i should download the drivers for it.
I got the drivers from here: [http://blog.datacompboy.ru/2009/07/12/saitek-p2500-linux-driver/](http://blog.datacompboy.ru/2009/07/12/saitek-p2500-linux-driver/)

after that i installed checkinstall.

In extracted the tar.bz2 file and then in it's folder i press F7to open the terminal, and then:
Make
Sudo checkinstall 
Results:
```
2 -  Name:    [ sp2500 ]
3 -  Version: [  ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ SP2500-0.9.0 (2) ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ sp2500 ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
/usr/bin/installwatch: eval: line 133: syntax error near unexpected token `('
/usr/bin/installwatch: eval: line 133: `echo /home/crimzoneyed/Downloads/SP2500-0.9.0 (2),/dev,/proc,/tmp,/var/tmp'
make -C /lib/modules/2.6.38-8-generic/build M=/home/crimzoneyed/Downloads/SP2500-0.9.0 (2) modules
/bin/sh: Syntax error: "(" unexpected
make: *** [modules] Error 2

****  Installation failed. Aborting package creation.
```


Oh and Hi I'm CrimzonEyed I'm new to the forum+ubuntu, and I'm a Windows to Ubuntu switcher.

---

### Post by Yellow Pasque on 2011-05-05
When I get home to my desktop machine, I will try to get this thing to build. I'm replying to subscribe to the thread.

---

### Post by CrimzonEyed on 2011-05-06
Pump bumped!

---

### Post by Jpenguin on 2011-05-06
I never got this driver to work with my my P2600, even after changing the ids

apply [http://belegdol.fedorapeople.org/p3200.patch](http://belegdol.fedorapeople.org/p3200.patch)

after the patvh, you might want to try whats in comment #9

---

