---
title: "mic not working, toshiba T325d, alc 265"
date: 2011-01-29
forum: Hardware
---

### Post by buddajah on 2011-01-29
i have read through the posts and tried some of the stuff i read there but i still am unable to get my mic working under linux.

initially i wanted to install 10.10 64 bit but that would not install on this system so i installed 10.04 64bit LTS instead.video and sound plaback works but the mic will not capture sound. the sound card is a realtec ALC 265. 

the system is a toshiba T235d-s1360. the sound card is a realtec ALC 269. i have tried checking setting and making adjustments with different mixers. no luck. i hope this isn't gonna be require some crazy kernel recompile for a microphone?

anyone know how to get this working?

---

### Post by buddajah on 2011-01-29
ok i hooked up an external microphone to it and it still does not work. there is no input by the mic. double check alsa mixer setting and every thing is set to max and enabled.

---

### Post by buddajah on 2011-01-30
after hours of searching i have the problem fixed. apparently the problem was in the default alsa install by ubuntu. all i can say for any sound issue is to check all your sound setting in your top bar and alsamixer in you terminal. if that fails there is an alsa script you can download from a post in this site. run it from the shell and it DL all the alsa files and reinstall alsa for you. this fixed my microphone issue. i can finally say good by to winblows. 

here is what worked for me:
[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

i hope this helps someone.

---

