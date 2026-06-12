---
title: "Problem with external sound card"
date: 2008-11-08
forum: Hardware
---

### Post by Col Matrix on 2008-11-08
Hi there folks, total and utter newbie here with a problem with his external sound card!

Never used anything apart from Windows until now. Trying to give Ubuntu a fair crack at winning me over. Still getting my head around Ubuntu so you'll have to be patient with me and really spell everything out in simple terms :(

If I can't get this card to work, chances are I'm going back to Windows...which would be a shame. So this is your chance to convert someone to Ubuntu! :D

Anyway, I've got a Sound Blaster Live! external USB sound card, model SB0490. It is recognised by Ubuntu, in that in Preferences>Sound I see entries for the card with OSS and ALSA.

I found a thread on here that mentioned the same model of card - [http://ubuntuforums.org/showthread.php?t=759147](http://ubuntuforums.org/showthread.php?t=759147) (I'd post there but it won't let me...?)

Anyway, here's the output of     
    * aplay -l
    * arecord -l
    * ~/.pulse/default.pa
    * output of pulseaudio when you run it from a terminal.

like the guy in that thread mentioned:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jonathan@jonathan-laptop:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
jonathan@jonathan-laptop:~$ ~/.pulse/default.pa
bash: /home/jonathan/.pulse/default.pa: Permission denied
jonathan@jonathan-laptop:~$ pulseaudio
W: ltdl-bind-now.c: Failed to find original dlopen loader.
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

Many thanks in advance.
Jonny

---

