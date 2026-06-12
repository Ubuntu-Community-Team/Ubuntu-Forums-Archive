---
title: "Want to Install New ATI Display Driver from ATI Site 10.5"
date: 2010-06-12
forum: Hardware
---

### Post by stumay on 2010-06-12
Need help with installing New ATI Driver from their website, 10.5, right now running some version (older) from the update within Ubuntu upon first boot.

Current version: 8.723.1-100408a-098580C-ATI



Thanks

---

### Post by stumay on 2010-06-13
[SIZE=4]Yello[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Will this work for uninstalling and installing ATI Driver from ATI?[/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Destructions: from "Wiki Page"[/SIZE]
[SIZE=4][/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]Latest update to package is in Lucid Repositories. [/SIZE]
[SIZE=4][/SIZE]
[SIZE=4]sudo apt-get update [/SIZE]
[SIZE=4]sudo apt-get install fglrx fglrx-amdcccle fglrx-dev fglrx-modaliases [/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4]If you get this message when running the apt-get install command: [/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]Building for architecture x86_64Module build for the currently running kernel was skipped since thekernel source for this kernel does not seem to be installed.update-initramfs: deferring update (trigger activated) [/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]Then you need the kernel source header package, so first you need to remove the fglrx and install source-headers and install fglrx again. Tidious I know :( [/SIZE]
[SIZE=4][/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]sudo apt-get remove fglrxsudo apt-get install linux-headers-`uname -r`sudo apt-get install fglrx [/SIZE]
[SIZE=4][/SIZE]
[SIZE=4][/SIZE] 
[SIZE=4]sudo aticonfig --initial [/SIZE]
[SIZE=4] [/SIZE]
[SIZE=4][/SIZE]
[SIZE=4]Reboot [/SIZE]

---

### Post by stumay on 2010-06-14
Okay, here's the feedback:

Downloaded from ATI/AMD website, the Proprietary driver: 10.5 which has the 8.732 driver
with OpenGL 4.0.

Uninstalled the previous Proprietary driver from the Hardware Manager inside Ubuntu (forgive me I'm new to Ubuntu so short on names) by the Applet and clicked on Remove. which worked flawlessly so far.  Then, installed the 10.5 driver for x86_64 bing bang boom installed as according to the instructions from the ATI/AMD site no problems whatsoever.

Instructions to install driver from ATI site: this is after uninstalling the other one.

open terminal

type: sudo sh ./ati-driver-installer-10-5-x86.x86_64.run
this brings up a temp folder on the leftside (don't touch it) then brings up a GUI window follow the instructions about three window changes  for Automatic Install then it will install while the GUI is open, you'll see progress bars then after it is done, click exit.
then reboot.

Have a good day

---

