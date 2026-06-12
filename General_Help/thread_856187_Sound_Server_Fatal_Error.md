---
title: "Sound Server Fatal Error"
date: 2008-07-11
forum: General Help
---

### Post by siabost on 2008-07-11
Hi,

Ubuntu 8.04LTS running KDE3.5 Desktop

I get the following error message in a box entitled "Error-Arts Message":
"Sound server fatal error. cpu overload, aborting"

My cpu is a PIII 933Mhz.

The message comes up shortly after boot up (but only sometimes) & normally when nothing is running apart from the desktop & Pidgin.

Ideas?

Thanks.

---

### Post by siabost on 2008-07-22
Addition to that posted above:
The PC is a Siemens unit and I have a Creative Soundblaster Live! PCI card installed. The sound was originally provided by a "Legacy" on-board device. I have this disabled in the BIOS & Soundblaster enabled.

This seems to make no difference as sometimes I have sound & other times not. I can have no sound from boot-up or it can fail as detailed above.

I have WIN2000K Pro, Ubuntu 8.04LTS (KDE Desktop) & Mandriva 2008 Spring installed on the HD. I have the problem (identical) on both Linux distributions but not on WIN2K.

The soundblaster card is far from unusual so does anyone have any ideas?

Any pointers gratefully received.

---

### Post by otisrobertson on 2008-09-05
Look at System Settings (in K menu) > Advanced tab > System Services.  See if alsa-utils is running and set to run at boot.  Setting this to run and to run at boot solved this very problem for me.

---

