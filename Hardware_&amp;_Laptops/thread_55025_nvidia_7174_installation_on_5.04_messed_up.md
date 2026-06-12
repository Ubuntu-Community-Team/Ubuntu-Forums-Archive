---
title: "nvidia 7174 installation on 5.04 messed up"
date: 2005-08-07
forum: Hardware &amp; Laptops
---

### Post by dolf on 2005-08-07
Hi everybody,

this morning, I was getting adventurous and trying to install the NVIDIA 7667 driver on top of my working 7174. In spite of all kernel header and kernel source files installed, the driver didn't compile. Setting SYSSRC=/usr/src/linux and going the manual way (NVIDIA...run --extract-only; cd NVIDIA.....pkg1/usr/src/nv; make) solved this part of the problem. I then did, in the extracted directory, checkinstall -D make install, which worked, but afterwards I couldn't start X anymore.

I have trouble with my Acer Aspire 1520 anyway, after leaving X, the console is usually all white and unreadable, so all failed attempts to start X mean rebooting (anybody got a solution for this?).

Alright, my /var/log/Xorg.0.log says

.......
(II) Initializing extension GLX

   *** If unresolved symbols were reported above, they might not
   *** be the reason for the server aborting.

Fatal server error:
Caught signal 11.  Server aborting

When libdri.a is loaded, then I get an additional message about an undefined symbol __glXgetActiveScreen (which is being defined by the libglxmesa.a that the nvidia driver installation moves away). Removing libdri.a doesn't solve the problem (I not only have to comment it in xorg.conf, but also move it into another directory, since the server seems to attempt to load all modules from /usr/X11R6/lib/modules/extensions, regardless of whether they're enabled in xorg.conf).

I then first extracted the backup that checkinstall had created. No improvement. I then did apt-get install --reinstall with the X server and the NVIDIA 7174 module packages. No improvement.

At the moment, I'm back to software rendering, having removed libglx.so from  /usr/X11R6/lib/modules/extensions. This one really seems to be the culprit.

I'm at my wit's end now - does anybody of you gentle folks out there have an idea what I might try to solve this?

Thanks a million, Dolfi

---

