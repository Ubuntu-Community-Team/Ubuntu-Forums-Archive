---
title: "Sound everywhere(?) except Flash"
date: 2007-04-19
forum: Hardware &amp; Laptops
---

### Post by shmeeter on 2007-04-19
Greets-

***********************************

EDIT - FIXED - I installed nspluginwrapper, following the guide at [http://ubuntuforums.org/showthread.php?t=341727](http://ubuntuforums.org/showthread.php?t=341727).  I'm sorry, I don't know how to link to a specific post.  Maybe that will work.  I googled ubuntu nspluginwrapper, and I think it's the first hit.

Anyway, now flash w/ sound works even in 32bit Firefox.

Thanks pinguin!

***********************************

Gateway 7510gx laptop
ATI IXP AC97 audio
Ubuntu 6.06 LTS Dapper Drake

I'm working on this install, and I've got pretty much everything working except for all the sound.  I asked this same question in "Gateway laptops in general," but I thought a new thread would be good.  Login sound, check.  Java sound in Firefox, check.  Sound in games, check.  Flash sound in Firefox, negative.  Haven't been able to test like an mp3, I think I need some codecs.  Edit - I confirmed that internet radio works in Rhythmbox.  So, just Flash?

I had previously done the whole alsa-oss thing.  For some reason, the system sounds would sometimes work and sometimes not. I installed alsamixergui, and disabled external amp, and that helped. Here are my mixer setting: Master on, Head(phones?) off, PCM on, Line off, CD off, Mic off, Mic Boost off, Video on, Phone on, IEC958 off, IEC958 Playb(ack?) AC97... on and on, PC speaker on, aux on, capture on, mix on, mix mono on, external amplifier off.

Thanks in advance!
Shmeeter

---

### Post by shmeeter on 2007-04-19
Hi all.

Well, did notice one thing.  I have both alsa-oss and ia32-alsa-oss.  Should I pick one or the other?  I already edited /etc/firefox/firefoxrc to read "FIREFOX_DSP=aoss."  Should I uninstall one of the two installed packages?  Also, is it possible to figure out if the aoss wrapper is even available for use?  It is a wrapper, right?

Thanks and good luck
Shmeeter

---

