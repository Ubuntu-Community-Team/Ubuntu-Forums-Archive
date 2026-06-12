---
title: "co-pilot GPS unit"
date: 2009-07-05
forum: Hardware
---

### Post by liesnomore on 2009-07-05
I run co-pilot under windows but since I installed ubuntu 9.4 I would like to have a GPS working.
The 9.4 version works very good on my laptop. I have toshiba portege M400 and everything  work fine.
I have 598U evdo from sprint and was installed better that in windows. My tablet pen works very good.
The best OS I have installed. I wonder if I could find a way to use Photoshop plug-in in Gimp or other graphic program.
I went to co-pilot web site, but could not find a driver(ALK Technologies).

---

### Post by liesnomore on 2009-07-05
My GPS is SU353. I found driver at website, but I am not much of a command line.
 there is a read me file of how to, but I am concern that my EVDO will stop working.
there is that read me file: 
To install driver - 
        make inst (The Makefile will check the module and compile and link it automatically. It will also remove 
                   the loaded USB-Serial driver) 
 
To uninstall driver - 
        make uninst 
 
To uninstall all drivers (including base driver) - 
        make uninst_all 
 
To remove module (*.o) files - 
        make clean 


Do I have to use some kind of terminal?
Thanks

---

### Post by liesnomore on 2009-07-06
I look at /dev/serial/by ID and found that my gps it is loading on port0 when the EVDO it is loading on port0 too and port1,port2,port3.Why it is my evdo taking all the ports and how do I make my gps to load on port other that 0. I could use some help here.
On the other note - I  use a compiz and mess up my system. Had to reinstall.

---

### Post by liesnomore on 2009-07-06
Bump

---

### Post by liesnomore on 2009-07-07
bump

---

