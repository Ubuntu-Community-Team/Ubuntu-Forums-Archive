---
title: "Question for real hackers: Skype over NX session"
date: 2008-09-17
forum: General Help
---

### Post by januszzz on 2008-09-17
Yay!

I've crafted NX terminal :-) it features:
- nxclient-2xterminalserver as a primary application,
- boot from usb on any x86 hardware,
- fits as low as 108MB with full glibc,
- has 2 independent NX sessions,
- one IceWM desktop with xterm (for those who still need bash),
- rdesktop (to proof that I CAN DO),
- printer server (CUPS),
- web browser (Dillo, mainly for CUPS),
- configs are written to separate rw partition to survive reboot,
- alsa sound support,
- Pulseaudio for remote sound,
- netfilter for geeks satisfied,
- its dumb proof (everything user can del is not needed for normal operations),
- netcat, ssh with hpn patch, rsync, acpi, wifi and 1000+ devices that are supported by the piece of code named linux kernel :-)

And now I want Skype on that too!

(EDIT: ok, not on NX terminal, but working on server.)

The problem is Skype supports only alsa, not pulse. I need pulse server on remote machine to put the sound to NX terminal (how to check its IP the best way anyway? I can just connect from anywhere). I also need microphone redirected from NX terminal to server.

While redirecting sound is not damn tough (it works perfectly on almost default setup), but using Skype to produce something right to Pulse is. And what about microphone? will I be able to redirect it back to the server through Pulse? I guess I can but how?

And about nxclient-2xterminalserver: yes, it has a button "Multimedia support" which does nothing what I would have a control on; sometimes works, more it doesn't.

I've spent too much coffee on this to quit prematurely :-) I'm seeking ideas!

Janusz.

---

