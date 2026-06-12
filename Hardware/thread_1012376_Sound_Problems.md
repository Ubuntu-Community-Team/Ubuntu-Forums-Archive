---
title: "Sound Problems"
date: 2008-12-15
forum: Hardware
---

### Post by lapses on 2008-12-15
I installed Ubuntu on my laptop a few days ago and everything was working fine. Then today I was playing around with various applications and compiz fusion and now suddenly the sound is gone. When I play anything all I can hear is a very low rustling sound.

I have tried booting up in different live CD's and the sound works, so I know the speakers are working.

Back in the ubuntu I created new users and logged in with their credentials. I thought maybe Id disabled something and a new account would have all the default settings - but that didn't work.

I have asked for help on another forum and they suggested

1) alsamixer
2) 'cat /dev/urandom > /dev/dsp'
3) alsaconf

So far none of these have worked, I was hoping maybe somebody here might be able to give me some help.

---

### Post by tommcd on 2008-12-16
First disable compiz. Then reboot and see if the sound comes back. If it does not, work your way through this troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
If you still can't get sound to work, then post the output of those commands as they are listed in that troubleshooting guide. The output of those commands should give enough info so that I (or someone else) can hopefully solve your problem.
Was this a real install of Ubuntu, or did you install Ubuntu in Windows using Wubi?

And welcome to the Ubuntu forums!

---

