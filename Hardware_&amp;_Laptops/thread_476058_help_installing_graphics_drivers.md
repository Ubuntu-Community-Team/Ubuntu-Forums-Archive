---
title: "help installing graphics drivers"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by linux noooob on 2007-06-16
ok so i got my intel graphics drivers from the intel website and yes it was meant for linux ok so when i go to the file  there is a file called install.sh and i am gessing that is how i install it. so the question is ho to i open and start it up to install??

---

### Post by jasmuz on 2007-06-17
On the console/terminal type: 
sh install.sh

---

### Post by linux noooob on 2007-06-17
Compiling new agpgart module...

ERROR: AGPGART module did not compile

Compiling DRM module...

ERROR: Kernel modules did not compile

The DRI drivers can not be installed without the latest kernel modules.
Installation will be aborted. See the dri.log file for information on
what went wrong.

what did i do?? it says that the kernel module is gdg does that have anything to do with it?
(note i have tow ubuntus thie first one was my original and the second was when the kernel was updated.)


hear is the contents of dri.log :  
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/andy/Desktop/dripkg/agpgart-2.0 modules
make: *** /lib/modules/2.6.15-26-386/build: No such file or directory.  Stop.
make: *** [default] Error 2
Makefile.linux:151: *** Cannot find a kernel config file.  Stop.

---

### Post by Diabolis on 2007-07-06
Open synaptic and look for this linux header: 2.6.15-26-386, After you install it, if you try to run install.sh, your dri.log file while change. Unfortunately this is where I'm stuck too.

---

