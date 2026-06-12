---
title: "System Sounds not working"
date: 2008-07-26
forum: General Help
---

### Post by oligray on 2008-07-26
my system sounds will not make any noise..

everything else is.. when i checked the only parts with anything set was login/logout and they didnt work and when i set any others they stayed silent up clicking play aswell

im on 8.04

---

### Post by ricardisimo on 2008-08-23
Same here... kind of. I tried putting several custom-made login and logout .wav files into the /usr/share/sounds folder (via superuser nautilus) as I did in the past with Dapper, Edgy and Feisty. No luck this time. The files are there, and the permissions say root, but the file icons carry the "unreadable" emblem on them for reasons unbeknown to me.

Not that it matters, since I couldn't use the original files in my home folder either. I tried exporting the wavs to the folder in question via audacity (in superuser mode) and that worked exactly once, on one file only. That is to say, I could preview the audio file once. I'll keep working on it and report back.

---

### Post by carolinason on 2008-08-23
see here
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207883](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/207883)
and
pulse audio is the new kid on the block.
[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

---

### Post by ricardisimo on 2008-08-26
Thanks for the reply. Pulseaudio seems like a tad too much work right now, just to hear Cachao on my login. I'm going to add my two cents to the bug report and hope for the best.

---

### Post by oligray on 2008-09-16
thanks for peoples replys 

im soo bad i completely forgot about that post and ive had nothing to do this after noon and was trying to work it out again and saw my post

so is pulseaudio going to fix it and my problems are within in ALSA

because sometimes my speakers dont work when i turn the computer on if i dont turn them on as it is booting at the right point

---

