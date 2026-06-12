---
title: "PCSC (smartcard daemon) vs HAL"
date: 2009-11-11
forum: Hardware
---

### Post by klimbermann on 2009-11-11
Hello all,

Today I discovered that my trusty OmniKey 4321 smart card reader (and hence the card inserted into it) can not be seen by my system (fully updated Karmic).

Turns out the PCSCD is not loading anymore at startup. I then dive right into /var/log to find the following in syslog:

> 
Nov 11 19:48:35 ogion pcscd: hotplug_libhal.c:490:HPRegisterForHotplugEvents() Could not initialise connection to hald.
Nov 11 19:48:35 ogion pcscd: hotplug_libhal.c:491:HPRegisterForHotplugEvents() Normally this means the HAL daemon (hald) is not running or not ready.


Apparently, when PCSCD tries to do its magic, HAL is not available (correct?). Eventually, though, HAL *will* get automatically loaded, but PCSCD will not; I have to sudo start it manually to use my smartcard.

There is no link to HAL in any of the rc*.d directories -- is something else responsible for loading it? PCSCD is there, always S50. I would be really happy to see PCSCD popping up on boot again though... Any suggestions?

(I returned to Ubuntu only recently -- with Karmic, to be exact -- because I needed Windows for work. I missed Gutsy, Hardy, Intrepid and Jaunty... quite a few things have changed in the meantime and some relearning is in order. I'm sorry if this is something really trivial.)

---

### Post by dengert on 2009-11-13
This apprears to be a timing problem with pcscd being started before hal is completly up. Adding a sleep 5 to the begining of /etc/init.d/pcscd appears to be a temporary circumvention.

---

### Post by klimbermann on 2009-11-17
> **dengert said:**
> This apprears to be a timing problem with pcscd being started before hal is completly up. Adding a sleep 5 to the begining of /etc/init.d/pcscd appears to be a temporary circumvention.

Thanks, your suggestion worked beautifully.
Marking the problem solved.

---

