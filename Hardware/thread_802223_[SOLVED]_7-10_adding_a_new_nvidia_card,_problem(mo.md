---
title: "[SOLVED] 7-10 adding a new nvidia card, problem(monitor i believe)."
date: 2008-05-21
forum: Hardware
---

### Post by fktt on 2008-05-21
So, i bought a nvidia 64mb fx5200 into another machine that used to only have a integrated via.

Once i installed the new piece of hardware,
it starts up with a:

[CENTER]
Attention
out of range
H:   .3K V:391.6Hz
[/CENTER]

Cant get past that obviously.

Now, what I've tried:
while booting, going to the grub menu and booting with the recovery option and:
'sudo dpkg-reconfigure xserver-xorg'

didn't work, so i tried to boot with a live cd and change the xorg.conf that way,
what i made sure of was to not have any resolutions over the maximum rez. of the old crappy generic monitor,
that would be 1024x768.

And made sure to remove the sync ranges from there.. didn't help either, so I'm stuck.
Now, if anybody has got some ideas, feel free to shoot them my way, would be much welcomed! ;)

**edited rev.1:**
Tried editing the /etc/usplash.conf didn't help. :(

**edited rev.2:**
Tried another older monitor, this one turns to power save mode: off mode,
or something and shuts it self down.. :(

**edited rev.3:**
[COLOR="Blue"]*with some more hacking of the Xorg.conf the problem magically fixed it self. ;)*[/COLOR]

---

