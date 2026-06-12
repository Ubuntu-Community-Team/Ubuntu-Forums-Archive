---
title: "Volume Control Wheel not working for 1 user but working for the second on notebook"
date: 2011-11-07
forum: Hardware
---

### Post by awmian on 2011-11-07
I am using ubuntu 10.04 lts on my acer aspire 2920.
Recently I disabled/uninstalled pulse and am using ALSA. Everything seems to be working fine except for 1 little glitch which I can't seem to figure out:

The volume control wheel on my laptop has no effect on the volume although I can manage volume through the gnome volume applet.
The volume control wheel works fine if I login as a different user.

Can anyone guide me on how to make the volume control wheel work on my own user profile. It seems that some configuration needs to be tweaked. I am not a linux geek but a linux fan and would appreciate some help here.

---

### Post by awmian on 2011-11-08
Bump

---

### Post by awmian on 2011-11-11
Bump

---

### Post by MoreOrLess on 2011-11-11
Is your user in the audio group?

---

### Post by awmian on 2011-11-12
> **MoreOrLess said:**
> Is your user in the audio group?
Yes

> asad@asad-laptop:~$ grep 'audio' /etc/group
audio:x:29:asad,amna,guest

I do get sound for all users. The only thing is that the volume wheel on my notebook does not work when I am logged on from MY user profile but works fine for ALL OTHER users

---

### Post by awmian on 2011-11-13
Hello...anyone ... someone ...

---

