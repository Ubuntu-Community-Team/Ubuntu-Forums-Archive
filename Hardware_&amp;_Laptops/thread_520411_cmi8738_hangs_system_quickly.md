---
title: "cmi8738 hangs system quickly"
date: 2007-08-08
forum: Hardware &amp; Laptops
---

### Post by davidsrsb on 2007-08-08
Feisty 7.04
I have a Dell core2duo that was having problems with the on board audio, so I installed a CMI8738 card. The on board sound is disabled in the bios.

The card work at start up and stays working until a sound juicer or a game with background sound makes it do some work. After 10s of seconds the application hangs and sound stops. The application can be killed, but alsa/esd is blocked and the machine has to be reset to get out of Ubuntu.

The card works fine under XP and on another Ubuntu 7.04 machine with AMD dual core cpu

lsmod shows that the snd-cmipci module is used.

---

### Post by davidsrsb on 2007-08-08
Update
The problem seems to be ESD hanging
Forcing alsa in system-pref-sound stops the hang.
I get a lot of stuttering on the audio when I move the mouse about.
This smells of an interrupt clash, I will try the other pci slot

---

### Post by davidsrsb on 2007-08-09
Chasnging the slot did not help.
Fixed with a bios update

---

