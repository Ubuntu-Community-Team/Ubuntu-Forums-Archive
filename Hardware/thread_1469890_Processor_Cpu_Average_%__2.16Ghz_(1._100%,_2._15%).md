---
title: "Processor Cpu Average % ? 2.16Ghz (1. 100%, 2. 15%)"
date: 2010-05-02
forum: Hardware
---

### Post by UbuNoob001 on 2010-05-02
Hey guys I have a inspiron 1545 2.16 ghz


My cpu usage was spiked at 100 and 90, only running firfox (said java was taking 94%). But now that I killed that process: 

CPU1: 100%
CPU2: 10-20% 

is it normal for one to be spiked like this? I am just running firefox (to write this), IM chat client, and system monitor. 


Fan keep running.

---

### Post by khelben1979 on 2010-05-02
Use the top command to check for processes which needs to get terminated. Otherwise, it can be slow video drivers which is being used.

```
man top
``` to see how it can be used.

---

### Post by UbuNoob001 on 2010-05-02
Okay, problem apears to be 1. Java and 2. Npviewer.bin

both of which take up 70% on processes. Not sure how to deal with this as vista never had this problem.

---

### Post by khelben1979 on 2010-05-02
It would be interesting to know which java supplier is being used by the system. I think that the java package from Sun Microsystems would work best, so you can check that up in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager") to see what you have installed.

---

