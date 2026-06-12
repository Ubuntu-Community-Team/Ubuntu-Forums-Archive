---
title: "Resume/reload alsa &amp; X"
date: 2005-11-08
forum: General Help
---

### Post by grinchy on 2005-11-08
Ok the problem I have is that any time I resume from a suspend, either to ram or disk, alsa no longer works and also some applications do not display properly, especially xine, ie blank screen

I can fix alsa buy running
sudo /etc/init.d/alsa force-reload

but this causes all applications that were using alsa to exit

to fix the later problem I restart X (<ctrl><alt><backspace>)

however this makes suspending a little pointless.

Any ideas?
I am using APM on an IBM T21 thinkpad

putting sudo /etc/init.d/alsa force-reload into my /etc/apm/resume.d directory as alsa-restore has no effect

---

