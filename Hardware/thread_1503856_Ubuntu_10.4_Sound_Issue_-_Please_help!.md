---
title: "Ubuntu 10.4 Sound Issue - Please help!"
date: 2010-06-07
forum: Hardware
---

### Post by Yehudah on 2010-06-07
I have installed Ubuntu 10.4 LTS onto my Dell 1536 AMD laptop. I've been struggling for two weeks with several issues. I'm not a newbie to Ubuntu, but I've become very frustrated with this version and I'm close to needing to go back to W7 (yeck).

I have surfed these and other forums for almost two weeks now and have used workarounds and supposed fixes that don't seem to  work. Here is one of my issues:

My sound settings will not save. When I go into Alsa Mixer and up the volumes and quit, they are saved after I reboot. I have run: alsactl store, and variants of it, to no avail. Every time I reboot, I have to go into Alsa Mixer to adjust the sound.

Can anyone assist me with this?

---

### Post by mörgæs on 2010-06-08
If you want to skip 10.04, why don't you install 9.10 in stead? It is finally getting stable.

---

### Post by Yehudah on 2010-06-08
Actually, I've tried other distributions, and for one reason or another, I don't care for any of them.

I used 9.04 for a while and liked it, but I'd like to stick with 10.4 because it's a pain to get everything set up and do it again... and again... and again.  LOL

---

### Post by mörgæs on 2010-06-08
If you install 9.10 then you most likely will need to do it only once :-)

Here is something on the sound in 10.04, if you want to go the long way:
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by lidex on 2010-06-09
Try this. Open this file for editing:
```
gksudo gedit /etc/pulse/default.pa
```
Scroll down to this line:
```
load-module module-device-restore
```
Comment it out so it looks like this:
```
#load-module module-device-restore
```
Save. Close. Logout/in.

No help? Try this.
Comment out line 372 in /etc/init.d/alsa-utils:
```
gksudo gedit /etc/init.d/alsa-utils
```
Change that line to look like this:
```
# mute_and_zero_levels "$TARGET_CARD" || EXITSTATUS=1
```
Reboot.

---

