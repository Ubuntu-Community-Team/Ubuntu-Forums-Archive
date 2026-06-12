---
title: "Why Nvidia Optimus is not supported under Linux?"
date: 2011-02-04
forum: Hardware
---

### Post by Sylslay on 2011-02-04
I am fun of nvidia GPU, and very disapointed wtith new 
nvidia GT 425 and nvidia GT 535 are not supported under linux!!!

So if I like buy new laptop for linux computing than I need buy at least 1 year old with nvifia GT 230M or GT 33OM, witch are fast enough for me :-)
GT230M vs GT330 tested on Ubuntu 10.10 with  usb-hdd and nvidia drivers.

score on [COLOR="Red"]glxgears: 21900 vs 24400[/COLOR], 

GT330M (samsung laptop with i5)  is 11 % faster than GT230M (toshiba laptop with P7450).

Any one knew about development of linux drivers for Nvidia Opitumus???:confused:

---

### Post by cchhrriiss121212 on 2011-02-04
Here is a good thread:
[http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html](http://forum.notebookreview.com/linux-compatibility-software/473915-no-support-nvidia-optimus-linux.html)
Looks like Nouveau is developing support for this, but Nvidia seem reluctant as it would be so much work.

---

### Post by cascade9 on 2011-02-04
> **Sylslay said:**
> I am fun of nvidia GPU, and very disapointed wtith new nvidia GT 425 and nvidia GT 535 are not supported under linux!!!

GT 425M is supported, and has been for a while- 

> Added  support for the following GPUs:
[LIST]
[LIST] GeForce GTS 450
  GeForce GTX 460M
  GeForce GT 415M
  GeForce GT 425M
  GeForce GT 420M
  GeForce GT 435M
  Quadro 2000
  Quadro 600 
[/LIST]
[/LIST]


[http://www.nvidia.com/object/linux-display-amd64-260.19.12-driver.html](http://www.nvidia.com/object/linux-display-amd64-260.19.12-driver.html)

GT 5XXM drivers will probably come out sooner or later.  

Unless nvidia has a major change of heart, there wil never be optimus dirvers for linux. As for Nouveau, it might get support for optimus at some time, but thats pointless (no VDPAU, poor 3D performance.....which are the main reasons to have an nvidia card IMO)

---

### Post by Sylslay on 2011-02-04
Nvidia Optimus IS NOT, as someone wrote before.

Additional Information.

Note that the list of supported GPU products is provided to indicate which GPUs are supported by a particular driver version. Some designs incorporating supported GPUs may not be compatible with the NVIDIA Linux driver: in particular, notebook and all-in-one desktop designs with switchable (hybrid) or Optimus graphics will not work if means to disable the integrated graphics in hardware are not available. Hardware designs will vary from manufacturer to manufacturer, so please consult with a system's manufacturer to determine whether that particular system is compatible.

THX cascade9: "Unless nvidia has a major change of heart, there wil never be optimus dirvers for linux."

---

### Post by nico77 on 2011-04-15
I noticed no-one has mentioned, in the whole Optimus nVidia debacle, how Apple have switched their new lines to ATI, keeping nVidia for the Air, MacBook and MacMini.
Which means in a year or two, Apple could go all ATI, and I'm not sure nVidia want to lose all that nice cash to be made there. So, will they pull their finger out and do something that works for OSX (and thus should be adaptable to *nix), or are they happy to see those go?
Anyone has an idea?

---

### Post by beew on 2011-04-15
Write to Nvidia. 
[http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278)

Even if they don't support gpu switching in Linux they should at least find a way for Linux users to use the Nvidia cards they paid for and Nvidia supposedly "support" with drivers. if not they may as well make the announcement that Nvidia no longer supports Linux on laptops so people wouldn't spend all the money only to find out they have bought a dud.

---

