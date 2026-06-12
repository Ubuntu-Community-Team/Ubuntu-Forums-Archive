---
title: "OpenGL does not work! Ati Mobile Radeon X1100"
date: 2009-06-21
forum: Hardware
---

### Post by TMKCodes on 2009-06-21
Okey so i am running kubuntu 9.04 and as there is no propierty drivers for my card i have to use the Radeon Free drivers, but my OpenGL does not work. Need it work one java game and for my own c++ stuff. 

```

tmkcodes@tmkcodes-laptop:~$ lshw -C display             
WARNING: you should run this program as super-user.
  *-display UNCLAIMED
       description: VGA compatible controller
       product: RS482 [Radeon Xpress 200M]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=66 mingnt=8
tmkcodes@tmkcodes-laptop:~$ glxinfo |grep -e "direct" -e "server" -e "OpenGL" -e "client"
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
client glx vendor string: SGI
client glx version string: 1.4
client glx extensions:
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX+/3DNow!+/SSE2 NO-TCL
OpenGL version string: 1.3 Mesa 7.4
OpenGL extensions:

```

---

