---
title: "No sound in Gnome"
date: 2004-11-18
forum: Hardware &amp; Laptops
---

### Post by boobytrapped on 2004-11-18
Hi All,  I recently installed Warty, and have an interesting problem.  Sound is working, I know that, because when the GDM login screen shows up I can hear the tab-beat sound effect.  Also, I can play wav files using 'aplay'.  However, none of the Gnome system sounds ever get realized, neither do I get any sound for rhythmbox, or mpg321 (which is not really a gnome app - so why should it be effected?)

Does anyone have any ideas on how to get sound to work in Gnome.  I think it must be some gnome configuration for my user that is not correctly setup.

FYI, I have a emu10k1 (SBLive!).  Also, I have a webcam plugged into usb, and the webcam has a built-in microphone -- it does show up in volume control.  Is it possible that gnome is trying route output to the webcam (being an alsa hardware)?

---

### Post by wande on 2004-11-18
If you have another soundcard in your motherboard then you have to configure your alsa and esd to use the second sound card (soudblaster live! in this case). Atleast I had this nasty problem. I solved it with editing my /etc/esound/esd.conf

```

mika@sarge:/etc/esound $ cat esd.conf
[esd]
auto_spawn=1
spawn_options=-d /dev/dsp1 -terminate -nobeeps -as 2
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```

-d /dev/dsp1 does the trick. Hope this helps.

---

### Post by boobytrapped on 2004-11-19
Okay, I have fixed it now.

Looking at the esd related packages I found out that libesd0 was installed and libesd-alsa0 was not.  Installing libesd-alsa0 fixed the problem.  

Does anyone on the forums know why libesd-alsa is not installed by default? (and why it conflicts with libesd0?).

Anyway, I am and old debian user who was lost for a while running other distributions (Gentoo).  Maybe Ubuntu can bring me back, so far it looks good.

---

