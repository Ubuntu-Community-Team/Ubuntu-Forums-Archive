---
title: "Computer restarts automatically"
date: 2009-11-12
forum: Hardware
---

### Post by vvinuv on 2009-11-12
Hi All
I am using a computer having core 2 quad processor and 4 GB memory and I have installed hardy. Now I am facing a non-trivial problem that when I try to run some programs, the computer works for some time and then reboot automatically. This happens when my program uses ~ 100% cpu. Could any body help me to find a solution?
Thanks
Vinu Vikram

---

### Post by wilee-nilee on 2009-11-12
> **vvinuv said:**
> Hi All
I am using a computer having core 2 quad processor and 4 GB memory and I have installed hardy. Now I am facing a non-trivial problem that when I try to run some programs, the computer works for some time and then reboot automatically. This happens when my program uses ~ 100% cpu. Could any body help me to find a solution?
Thanks
Vinu Vikram

Are the same programs causing this and if so what are they. This is a strange problem. Is it actually rebooting or going to the login screen?

---

### Post by JBAlaska on 2009-11-12
Check to see if your CPU is getting to hot, your computer may be shutting down due to this condition.

---

### Post by baskar007 on 2009-11-12
Yeah, this may happen due to HOT CHIPS.
remove side cover of your CPU and then try to power on .

---

### Post by underquark on 2009-11-12
Immediately after a crash, restart and (press F2 or whatever for your system) enter the BIOS.  See if there is a CPU temperature reading in your BIOS.  Removing the PC cover alone won't necessarily bring down the CPU temperature as airflow is important.  Consider fitting better cooling in any case for a quad-core system.

---

### Post by mpcengineering on 2009-11-12
Very likely sounds like overheating to me too, you might want to try out lm-sensors

[http://www.connectedinternet.co.uk/2009/05/24/monitor-cpu-temperatures-in-ubuntu/](http://www.connectedinternet.co.uk/2009/05/24/monitor-cpu-temperatures-in-ubuntu/)

---

