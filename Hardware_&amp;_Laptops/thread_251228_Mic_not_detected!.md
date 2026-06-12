---
title: "Mic not detected!"
date: 2006-09-05
forum: Hardware &amp; Laptops
---

### Post by kedarm on 2006-09-05
Hi!

I just installed Kubuntu 6.06 and installed Skype, however, it does not detect the microphone. All it says is "Problem with the sound device".

I have a Dell Inspiron 600m

Please help! Thanks!

---

### Post by odzx on 2007-02-15
similar problem in edgy x86_64.
aplay -l gives this output:
> **** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
amixer. this output:
> Simple mixer control 'Master',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 27
  Mono:
  Front Left: Playback 27 [100%] [on]
  Front Right: Playback 27 [100%] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%]
  Front Right: Playback 255 [100%]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 20
  Front Left: Capture 20 [100%] [on]
  Front Right: Capture 20 [100%] [on]
alsamixer does not show me any mic, just "capture" and playback.
i tried pluging the mic both in line-in and mic-in sockets and got no results.
any ideas were to start looking?

---

### Post by odzx on 2007-02-18
some screenshots to make it more clear:
[http://www.23hq.com/odzx/photo/1672975/view-large]("http://www.23hq.com/odzx/photo/1672975/view-large")
[http://www.23hq.com/odzx/photo/1672977/view-large]("http://www.23hq.com/odzx/photo/1672977/view-large")
[http://www.23hq.com/odzx/photo/1672978/view-large]("http://www.23hq.com/odzx/photo/1672978/view-large")
 already compiled alsa 1.0.13
any ideas will be appreciated.

---

### Post by Yumi on 2007-02-28
Same problem. Downloaded and reinstalled Edgy today. Doppelclick on Speaker-Symbol opens alsamixer window but no "Capture" tab.

Running alsamixer from terminal and unmuting speaker in capture I have no vertical volume bar.

Seems my microphone is not recognised. Was working before with Edgy.
Michael

---

### Post by odzx on 2007-04-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/80531](https://bugs.launchpad.net/ubuntu/+bug/80531) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				same problem for me even after a fresh install of feisty. i actualy tried other distros as well. the same thing happend with mandriva and with knoppix. the mic is not detected and alsamixer looks the same.
the only solution that partially worked for me was recompiling the last alsa but after that i could not get sound in flash within firefox and had some other minor sound issues, so I'm reluctant to try that again, just to get my mic to work. there are some suggestions in the bug report above, but non worked for me.

---

