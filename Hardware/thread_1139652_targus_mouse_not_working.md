---
title: "targus mouse not working"
date: 2009-04-27
forum: Hardware
---

### Post by 10ghost on 2009-04-27
i just got a new mouse(brand targus). on plugging it to the usb port i realised that it was not working. so i decided to type the command lsusb on the terminal . this was the result

 Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 003: ID 05b8:3091 Agiler, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 


the line Bus 003 Device 003: ID 05b8:3091 Agiler, Inc.
showed that tit recognised that the mouse was connected but
i dont know why it was not working
i tried the mouse on ubuntu 7.10 and it worked 
but it did not work on ubuntu 8.04

---

### Post by 10ghost on 2009-04-27
please can some one help me with this
if ones mouse is not working what are th various options one can use to correct this 
please i need this help badly

---

### Post by brainsonfire on 2009-07-16
its a kernel issue, its been fixed in 2.6.30.1.

download the 2.6.30.1 kernel from kernel.org then follow this guide from step 3 [https://wiki.ubuntu.com/KernelTeam/GitKernelBuild](https://wiki.ubuntu.com/KernelTeam/GitKernelBuild)

dont worry, its a piece of cake. if you have nvidia graphics and dpkg complains about nvidia-common during postinstall, just ignore it. after reboot just reinstall the driver.

may the ubuntu be with you

---

