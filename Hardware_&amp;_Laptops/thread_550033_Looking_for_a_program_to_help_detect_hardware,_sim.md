---
title: "Looking for a program to help detect hardware, similar to CPU-Z"
date: 2007-09-13
forum: Hardware &amp; Laptops
---

### Post by bg1256 on 2007-09-13
While using Windows, the program CP-Z was very helpful, as it gives very specific hardware details, not limited to CPU specs.  And I am looking for something like it for Linux.  I have installed cpuid from the repo, and it's great for viewing processor specs, but I'd like something more comprehensive.

For example, I'm shopping for RAM to add to my computer, and I'd like to be able to view what's in mine now without taking a look inside or booting into windows.

System Preferences -> Hardware Information yields a bunch of unknowns and isn't helpful for me.

If anyone knows of a program, command, etc. that could help me out, I would greatly appreciate it.

---

### Post by reckless2k2 on 2007-09-13
look into the /proc directory

if you look in there you can run a  bunch of commands like:

cat /proc/cpuinfo

from the terminal...they have memory and all..who's that?

---

### Post by bg1256 on 2007-09-13
Thanks, that's quite helpful for cpuinfo.  I'll keep tinkering to see if it will display RAM info.

Cool blog by the way.

cat /proc/meminfo gives a detailed output of the memory being used.  

However, I am looking for details specific to my hardware, such as the frequency of the stick of RAM I have installed, etc.

---

### Post by reckless2k2 on 2007-09-13
there is a memory one in there too i just can't remember it....

cat /proc/mem

i think


[http://www.idevelopment.info/data/Unix/General_UNIX/GENERAL_TheProcFilesystem.shtml](http://www.idevelopment.info/data/Unix/General_UNIX/GENERAL_TheProcFilesystem.shtml)

---

### Post by dabl on 2007-09-13
```
hwinfo
```

Can't remember if it is installed by default or you have to apt-get it.  :)

---

