---
title: "Compaq CQ61 sounds in ubuntu 9.10"
date: 2010-01-23
forum: Hardware
---

### Post by elliotbeken on 2010-01-23
hi there, 

i have got a new compaq laptop (CQ61) and my sound didnt work through the speakers but it did through the headphones.

i looked for a solution on google and came across one 

to fix the sound you:

1.open the terminal

2.type: sudo gedit /etc/modprobe.d/alsa-base.conf

3.then add these four lines to the bottom

options snd slots=snd-hda-intel
options snd-hda-intel model=hp-m4
alias snd-card-0 snd-hda-intel
options snd-hda-intel enable_msi=1 



hope this helps :P

---

### Post by MichaelSM on 2010-02-18
WOW elliotbeken!!!

Quickest and best fix ever.

Two small things:

1. Always acknowledge the fix's actual source if you can identify it.

2. Reboot.

There will be thousands of users struggling with this non-recognition of sound chip issue.

Thank you.

Mike.

---

