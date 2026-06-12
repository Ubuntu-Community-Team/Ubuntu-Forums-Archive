---
title: "Laptop sound dies during login"
date: 2009-03-30
forum: Hardware
---

### Post by tmeSiS on 2009-03-30
Hi everyone. I hate having a first post as a question at a forum, but I am afraid I have no choice. After five hours over three days of trying to solve this by myself, I am nowhere, so here goes:

After recently (two months or so ago) converted my desktop to Ubuntu Intrepid and I love it. Being the guy I am, I convinced my parents (after their Windows problems) to turn their laptop into Intrepid as well. Here's the problem: the login screen has sound, and after logging in, half of the welcome sound plays, before being cut off. No sound occurs after that, but a reboot of Xserver does play the 'ready-to-login' sound again.

I am wondering what might be happening during login that would kill my sound. The laptop in question is a Toshiba Satellite A70 - one which reportedly has problems with sound, although none of the fixes proposed seem to help (can't find them right now).

What it is not:
[LIST]
[*]a muted ALSA channel - alsamixer shows only a MASTER channel (seems suspicious)
[*]no permissions to use the audio device
[*]sound turned down or blown speakers - sound works at login screen
[/LIST]

If anyone could help, I would be much obliged.

Thanks,
Sandy Maguire

---

### Post by EvilRobot on 2009-05-15
Hi I'm also having the exact same problem with Hardy Heron on my dad's Toshiba Satellite A70 and can't figure out what the problem is, although at one point after a reboot the sound did continue to work past the login but then firefox crashed and the sound stopped working again. I wonder if installing Jaunty would fix the problem... guess I'll try it and see if that works. I'll keep you posted if it works.

---

### Post by EvilRobot on 2009-05-16
Well I installed Jaunty on my dad's Toshiba Satellite A70 and the audio now works properly. Hope this will work for you as well, best of luck.

---

