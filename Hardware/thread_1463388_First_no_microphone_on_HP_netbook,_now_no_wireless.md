---
title: "First no microphone on HP netbook, now no wireless"
date: 2010-04-26
forum: Hardware
---

### Post by mormit on 2010-04-26
The patient: HP mini 110 running Ubuntu 9.10 desktop.

The only issue I had was a non-working microphone. Didn't work in system testing, recorder, Skype. After some searching here I did the following:
*  installed linux-backports-modules-karmic
*  installed linux-backports-modules-alsa-karmic-generic
* in gedit added the line: options snd-hda-intel model=auto

Rebooted and the microphone now works. The wireless however has stopped. I'm currently connected via LAN line. The wireles uses Broadcom 802.11 Linux STA wireless driver which is showing activated but not in use.

Ideas? Thanks.


Update: Upgraded to 10.4 and both are working. I like easy fixes.

---

