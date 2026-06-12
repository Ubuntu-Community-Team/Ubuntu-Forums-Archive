---
title: "lirc: mce transmitter (blaster) compatibility"
date: 2011-08-14
forum: Hardware
---

### Post by Bertrandization on 2011-08-14
Hi,

Does anyone know whether irsend can only transmit a proper subset of what lircd receieves? (Or whether the "lsusb 1934:5168" (HP MCE compatible) device can transmit only a proper subset of what is receives?)

When irsend-ing using the /usr/share/lirc/extras/transmitters/scientificatlanta file, there is a red flash. It appears to work. I presume it is sending the signal.

Unfortunately, I do not own a scientificatlanta, and do not want to send this signal.

I own an NEC projector, and would like to transmit some of the signals in [http://lirc.sourceforge.net/remotes/nec/RC-6051](http://lirc.sourceforge.net/remotes/nec/RC-6051)

irw indicates these signals are correctly received.

When irsend-ing using the RC-6051, no error is received, but no signal appears to be getting sent. (There is no red flash on the blaster; the projector ignores it.)

Many thanks.

---

