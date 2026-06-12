---
title: "[SOLVED] Sound very quiet in gutsy"
date: 2007-11-06
forum: Hardware &amp; Laptops
---

### Post by bharris25 on 2007-11-06
I have a Toshiba Satellite A105-S4104.  It has a Realtek 860 sound card in it and it has sound but it's very quiet.  Had the same problem with Linux Mint and Feisty but both were fixed with the update but an update has yet to fix Gutsy I have played with AlsaMixer but everything is maxed out and I have yet to find someone with the exact same problem I have been having

Found this and it worked after reboot:
 Originally Posted by jekylczar  View Post
i fixed it...here was the solution....

adding to /etc/modprobe.d/alsa-base

options snd-hda-intel model=3stack

---

### Post by henklaak on 2007-11-06
Ok, all's well that ends well. There is a handy function on this forum to mark your thread as solved.
Saves others the bother to read an unanswered thread.

Regards, Henk.

---

