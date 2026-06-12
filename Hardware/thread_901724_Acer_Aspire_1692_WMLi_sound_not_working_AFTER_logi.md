---
title: "Acer Aspire 1692 WMLi sound not working AFTER login"
date: 2008-08-26
forum: Hardware
---

### Post by oz457 on 2008-08-26
Hello all,

I'm very desperate as I have been trying to make the sound card work into ubuntu with kernel Linux kurt-desktop 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux
on my Acer Aspire 1692.
I just cannot understand why I have drum sounds at the login welcome screen before actually logging in, but after logging into ubutu, there is no sound any more.

I have been playing around with switches in the volume control settings, but none worked. Followed many links regarding this issue, disabling/enabling the external amplifier switch, etc. etc.
I just don't know what to choose from the volume controller:
I can choose between:
Intel ICH6 (Alsa Mixer)
Conexant id 30 (OSS Mixer)
Playback: ALSA PCM on front:0 ...
and some capture devices.

But none works. 
If there is someone in cyberspace who has been succesfull in making the sound card work on their Acer ASPIRE 1692 WMLi DDR2 machine, 
please send me your configuration in 
/etc/modprobe.d/alsa-base
and any other file configuration.

I guess Ubuntu starts to read configuration files and some kind of driver starts to interfere with the sound card once logging in, because there is ACTUALLY sound at the damn login screen. 
I have been searching around for about 1 week now, but nothing seems to work. 

Any help appreciated. 

Thanks

---

### Post by oz457 on 2008-08-27
Bump! 
Anybody can help me with this?

---

### Post by hessiess on 2008-08-27
run 'alsamixer' is anything muted?

set everything to auto or alsa in the sound config

---

### Post by jwlutz on 2008-08-27
I'm having the same trouble on an older desktop.  My new HP 530 laptop works just fine.  Saw the problem in an archieve post, but not a solution.  Ubuntu will not play CD's or sound on the web.  Just the drum sounds at login.  I did not load with the speakers connected.  Don't know if that would make a difference or not.

---

