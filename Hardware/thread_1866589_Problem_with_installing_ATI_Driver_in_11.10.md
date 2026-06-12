---
title: "Problem with installing ATI Driver in 11.10"
date: 2011-10-21
forum: Hardware
---

### Post by emanamini on 2011-10-21
Hi there
I have a problem for installing ATI driver
Now I can find ati/amd proprietary fglrx graphics driver (post-release updates but when I try to active it the program start to download something and after a while return this error


sorry,installation of this driver failed.
please have a look at the log file for details:/var/log/jockey.log
```

#/var/log/jockey.log
[B]odulesDriverDB instance at 0x1ba5128> about HardwareID(‘modalias’, ‘input:b0003v413Cp8161e0111-e0,1,4,11,14,k71,72,73,74,75,77,79,7A,7B,7C,7D,7E,7F,80,81,82,83,84,85,86,87,88,89,8A,B7,B8,B9,BA,BB,BC,BD,BE,BF,C0,C1,C2,F0,ram4,l0,1,2,sfw’)
2011-10-21 13:28:05,405 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘evbug’}
2011-10-21 13:28:05,405 DEBUG: no corresponding handler available for {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘evbug’, ‘jockey_handler’: ‘KernelModuleHandler’}
2011-10-21 13:28:05,405 DEBUG: querying driver db about HardwareID(‘modalias’, ‘acpiRazzNP0100:’)
2011-10-21 13:28:05,405 DEBUG: querying driver db about HardwareID(‘modalias’, ‘input:b0003v0C45p6417eA112-e0,1,kD4,ramlsfw’)
2011-10-21 13:28:05,406 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘evbug’}
2011-10-21 13:28:05,406 DEBUG: no corresponding handler available for {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘evbug’, ‘jockey_handler’: ‘KernelModuleHandler’}
2011-10-21 13:28:05,406 DEBUG: querying driver db about HardwareID(‘modalias’, ‘pci:v00008086d00002C81sv00008086sd00008086bc06sc00i00&#8242;)
2011-10-21 13:28:05,414 DEBUG: querying driver db about HardwareID(‘modalias’, ‘input:b0019v0000p0003e0000-e0,1,k8E,ramlsfw’)
2011-10-21 13:28:05,415 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘evbug’}
&#1778;&#1776;&#1777;&#1777;-&#1777;&#1776;-&#1778;&#1777; &#1777;&#1779;:&#1778;&#1784;:&#1776;&#1781;,&#1780;&#1779;&#1782; DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘fglrx_updates’, ‘package’: ‘fglrx-updates’}
2011-10-21 13:28:05,856 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-21 13:28:05,857 DEBUG: fglrx_updates is not the alternative in use
2011-10-21 13:28:05,436 DEBUG: found match in handler pool xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-21 13:28:05,862 WARNING: modinfo for module fglrx_updates failed: ERROR: modinfo: could not find module fglrx_updates

2011-10-21 13:28:05,869 DEBUG: fglrx.available: falling back to default
2011-10-21 13:28:05,939 DEBUG: fglrx.enabled(fglrx_updates): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-21 13:28:05,940 DEBUG: fglrx_updates is not the alternative in use
2011-10-21 13:28:05,899 DEBUG: got handler xorg:fglrx_updates([FglrxDriverUpdate, nonfree, disabled] ATI/AMD proprietary FGLRX graphics driver (post-release updates))
2011-10-21 13:28:05,940 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘fglrx’, ‘package’: ‘fglrx’}
2011-10-21 13:28:05,981 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-21 13:28:05,981 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking
2011-10-21 13:28:05,941 DEBUG: found match in handler pool xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-21 13:28:06,236 DEBUG: fglrx.available: falling back to default
2011-10-21 13:28:06,305 DEBUG: fglrx.enabled(fglrx): target_alt /usr/lib/fglrx/ld.so.conf current_alt /usr/lib/fglrx/ld.so.conf other target alt /usr/lib/fglrx/alt_ld.so.conf other current alt /usr/lib/fglrx/alt_ld.so.conf
2011-10-21 13:28:06,305 DEBUG: XorgDriverHandler(%s, %s).enabled(): No X.org driver set, not checking

2011-10-21 13:28:06,265 DEBUG: got handler xorg:fglrx([FglrxDriver, nonfree, enabled] ATI/AMD proprietary FGLRX graphics driver)
2011-10-21 13:28:06,555 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘radeon’}
2011-10-21 13:28:06,555 DEBUG: no corresponding handler available for {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘radeon’, ‘jockey_handler’: ‘KernelModuleHandler’}
2011-10-21 13:28:06,555 DEBUG: searching handler for driver ID {‘driver_type’: ‘kernel_module’, ‘kernel_module’: ‘fglrx’}[/B]

```Thanks for your Help

---

### Post by snapsta on 2011-10-24
I am having the same problem, any clues? (I am also having trouble with my external monitor freezing intermittently but I am not sure if that is related to not being able to install the updates).

FYI: I have a MacBook 8,2

---

### Post by giuspen on 2011-10-24
same problem here, I have a Packard Bell EasyNote LJ75

---

### Post by gekkos on 2011-11-22
Same problem here, i have a MSI EX610

---

### Post by Mark Phelps on 2011-11-23
If you're presented with two versions, do NOT use the post-release version; use the other one.

---

### Post by gabrielaca on 2011-11-23
Mark Phelps is rigth, DONT install post-realease version; now this helped me fix this (by Cynical)

I just dealt with this problem myself. Here is the easy fix for it.

_in Ubuntu 11.10 unity 3D_


Hit ALT+F2 in order to get to the terminal (ALT+F7 will take you back to the desktop)

1. Remove fglrx related packages
Code:

> sudo apt-get purge fglrx*

2. Delete xorg.conf
Code:

> sudo rm /etc/X11/xorg.conf

3. Reinstall xorg components
Code:

> sudo apt-get install --reinstall xserver-xorg-core libgl1-mesa-glx:i386 libgl1-mesa-dri:i386 libgl1-mesa-glx:amd64 libgl1-mesa-dri:amd64

4. Reconfigure Xorg
Code:

> sudo dpkg-reconfigure xserver-xorg

and finally

5. Reboot
Code:

> sudo reboot

 :KS _**thanks goes to Cynical.**_ :KS

---

