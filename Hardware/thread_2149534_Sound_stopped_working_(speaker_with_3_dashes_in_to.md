---
title: "Sound stopped working (speaker with 3 dashes in toolbar)"
date: 2013-05-29
forum: Hardware
---

### Post by Darghon on 2013-05-29
(This topic might need to be moved to software, not sure)

Hello all,

I have a laptop with Ubuntu 12.04 installed.
It has been working great for over a year now, and about 2 days ago, I accidently changed my homefolder's folder and file permissions (a script that was seposed to run on a different folder).
I've restored my mistake to the best of my abilities, but as a result, my sound no longer works. I get no audio anymore from the laptop.

I've tried deleting the .pulse and .pulse-cookie folders in my homefolder, but this did not work...
I've tried reinstalling pulseaudio and alsa-base, but this didn't work either.

The only thing I've managed to do now, is somehow remove the audio widget from my system toolbar.

Can anyone help me resolve this issue? and as a added question, restore the audio widget in my system toolbar?

Thanks in advance

---

### Post by ohnonot on 2013-05-29
how about creating a new user and moving needed data?
so many things can have gone awry when that mistake happened... 
and since it was "only" the home folder, reinstalling anything should not have been necessary.

---

### Post by CatKiller on 2013-05-29
pulseaudio --start
in a Terminal should at least help you pinpoint the problem.

---

### Post by Darghon on 2013-05-29
Well, either several reboots, or the fact that I logged on as a different user, has detected my sound card again.
For now, the widget is still missing from my toolbar (but I re-installed indicator-sound or something)

And I'm happy to announce that I can play sounds again.

thx for the help :)

---

