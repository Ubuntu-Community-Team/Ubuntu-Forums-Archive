---
title: "compiling hplip"
date: 2005-10-11
forum: Hardware &amp; Laptops
---

### Post by GameManK on 2005-10-11
i'm trying to set up my hp deskjet 940c.

when i install hpijs from the repositories, it doesn't show up as a driver choice when setting up CUPS (gimp-print and a couple others are there)

when i install hplip (version 0.8.7)from the repositories, the driver database doesnt show up at all, and then KControl crashes.

I downloaded the source from hp's site (version 0.9.5) to try to compile it.
./configure and make go smoothly, but sudo make install ends with the following:

/bin/sh: /chkconfig: No such file or directory
make[3]: *** [install-data-hook] Error 127
make[3]: Leaving directory `/home/yuriy/mydocs/source/hplip-0.9.5'
make[2]: *** [install-data-am] Error 2
make[2]: Leaving directory `/home/yuriy/mydocs/source/hplip-0.9.5'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/yuriy/mydocs/source/hplip-0.9.5'
make: *** [install-recursive] Error 1

the instructions say something about chkconfig:
2. The HPLIP startup/shutdown script is Red Hat (chkconfig) and LSB
    (install_initd) compliant. If your distribution is not compliant the script may not work. 

which makes it sound like i can't compile it on my kubuntu system.

any ideas?

---

### Post by mlomker on 2005-10-11
> i'm trying to set up my hp deskjet 940c.


I guess I'm misunderstanding something, because the 940C driver comes preinstalled on both Hoary and Breezy.  You go into the Control Center under Peripherals, Printers, and select to add your printer and you don't get the HP printers as an option?

---

### Post by GameManK on 2005-10-11
the printer choice is there, but i want the best driver, which is hpijs/hplip and it's not there (after clicking next on that screen)

Edit: looked more carefully at your screenshot. On yours it shows up right there, but on mine only one choice of 940c shows up there, and 4 choices of drivers show up on the next screen but not hpijs

---

### Post by mlomker on 2005-10-11
> 4 choices of drivers show up on the next screen but not hpijs

I just took a look in Synaptic.  Do you have the **hpijs** and **foomatic-db-hpijs** packages installed?  I'm showing a group of **hplip** packages as well, but I do not have them installed.

---

### Post by GameManK on 2005-10-11
[QUOTE=GameManK]when i install hpijs from the repositories, it doesn't show up as a driver choice when setting up CUPS (gimp-print and a couple others are there)

when i install hplip (version 0.8.7)from the repositories, the driver database doesnt show up at all, and then KControl crashes.[/QUOTE]
^

EDIT: actually, just realized that description is wrong.  with hplip is when things went fine but the right driver didnt show up.  same thing with hpijs only.  with foomatic-db-hpijs, it would crash, and as i understand that package is needed to communicate with hpijs which is why hpijs doesnt show up when thats the only one installed.

as i understand hplip is the newest, most full-featured one which is why i want to get the newest version of that working, but any ideas to get foomatic-db-hpijs working would be great as well

---

### Post by mlomker on 2005-10-11
> any ideas to get foomatic-db-hpijs working would be great as well

I don't know, but the foomatic setup is what Ubuntu seems to come with out of the box.  Maybe you could reinstall that combination and start another thread with the errors (or crash info as the case may be).  I know there are some cups logs and whatnot that can be located.

Were you planning to upgrade to Breezy this weekend?  I made the move last weekend and it  has been stable enough for me.  Perhaps the newer packages in Breezy will solve your problem.

---

### Post by GameManK on 2005-10-11
restarted cups again and now it's there (with hplip 0.8.7 installed).

i rebooted earlier and it didnt help...
oh well thanks anyway. and yeah i'll upgrade to breezy.

---

