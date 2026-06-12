---
title: "Fresh Intrepid install and xorg doesn't works with 3D graphcis"
date: 2009-03-20
forum: Installation &amp; Upgrades
---

### Post by rjdsantos on 2009-03-20
Hi, I have a fresh Ubuntu 8.10 (Intrepid) install, almost 1 week, and until now after some updates by apt-get and Synaptics I'm have problems yet with my xorg and video card. :(

The glxinfo and glxgears gets the follow an error:

name of display: :0.0
X Error of failed request:  BadRequest (invalid request code or no such operation)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  19 (X_GLXQueryServerString)
  Serial number of failed request:  10
  Current serial number in output stream:  10

What's is wrong??

Attached follows the xorg.conf, Xorg.0.log, lspci, lshal and hwinfo.

Tks in advance !

---

### Post by rjdsantos on 2009-03-20
[UPDATE] Problem resolved. Follow solution (very interesting):

I found that error inside Xorg.0.log
...
(II) intel(0): Kernel reported 363776 total, 11777 used
(II) intel(0): I830CheckAvailableMemory: 1407996 kB available
[B](EE) intel(0): [dri] I830CheckDRIAvailable failed because of a version mismatch.
[dri] libDRI version is 5.0.0 but version 5.4.x is needed.
[dri] Disabling DRI.[/B]
...

So, the real problem is that the main driver, that have role to enable "direct 3D rendering", doesn't active. ](*,)

After this, the first search was focusing in the version of libDRI but don't make any sense. The instalation was fresh and up to date.

Searching more, I found a thread in another forum with a similar problem were the solution was uninstall all packages related to ATI Video Cards GPL drivers, fglrx. Cause: This specific ATI driver conflicts with Intel driver! :idea:

After removal (and purge) of packages (xorg-driver-fglrx), the problem was resolved. :popcorn:

---

### Post by laizer on 2009-04-05
Thanks for the solution.  
I'm running Intrepid on a Dell 6400 (1505e) with the Intel 945GM graphics hardware.  All OpenGL programs (glxgears, blender) had been giving me the same errors you were getting.  
I followed your solution 
*sudo apt-get remove --purge xorg-driver-fglrx*
rebooted X
and everything running happily.

Thanks!

---

