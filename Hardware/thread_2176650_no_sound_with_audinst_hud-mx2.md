---
title: "no sound with audinst hud-mx2"
date: 2013-09-25
forum: Hardware
---

### Post by lessless2 on 2013-09-25
Hi! I'm trying to get Audinst HUD-MX2 working on Ubuntu 13.04, because of there is no sound out of the box. 
I tried to select it manuall in the Deadbeef preferences and the indicator on  goes green while music is playing, but still no any  sound produced. This seems to be known issue:
[http://comments.gmane.org/gmane.linux.alsa.devel/109855](http://comments.gmane.org/gmane.linux.alsa.devel/109855)
[http://forums.linuxmint.com/viewtopic.php?f=49&t=128478](http://forums.linuxmint.com/viewtopic.php?f=49&t=128478)

but I do not understand what I need to do to in my curren Ubuntu to just listen to the music. Please help me :)

p.s. my `aplay -l` listing

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC887-VD Analog [ALC887-VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC887-VD Digital [ALC887-VD Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 10: HDMI 4 [HDMI 4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 11: HDMI 5 [HDMI 5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HUDmx2 [Audinst HUD-mx2], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HUDmx2 [Audinst HUD-mx2], device 1: USB Audio [USB Audio #1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and alasmixer screenshot

[IMG]http://i.imgur.com/ypS1wDc.png[/IMG]

---

