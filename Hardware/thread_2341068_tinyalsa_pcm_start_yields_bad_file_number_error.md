---
title: "tinyalsa: pcm_start yields bad file number error"
date: 2016-10-24
forum: Hardware
---

### Post by vaselinessa on 2016-10-24
[COLOR=#242729][FONT=Arial]I'm attempting a barebones program to use tinyalsa, but pcm_start always fails, returning -1 and setting errno to 9 (EBADF, i.e. bad file number). The call to pcm_open before this returns a non-null pointer, but it sets errno to 22.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]There appears to be no documentation for tinyalsa, so I'm having trouble understanding what I'm supposed to do. I based my program on an example from alsa (not tinyalsa), and I've read the header files for tinyalsa. Can anyone provide any guidance?
[/FONT][/COLOR]
```
[COLOR=#303336]pcm [/COLOR][COLOR=#303336]*[/COLOR][COLOR=#303336] dev [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336] pcm_open[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]1[/COLOR][COLOR=#303336],[/COLOR][COLOR=#7D2727]0[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] PCM_OUT[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336]&[/COLOR][COLOR=#303336]config[/COLOR][COLOR=#303336]);[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#101094]if[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]err [/COLOR][COLOR=#303336]=[/COLOR][COLOR=#303336] pcm_start[/COLOR][COLOR=#303336]([/COLOR][COLOR=#303336]dev[/COLOR][COLOR=#303336]))[/COLOR][COLOR=#303336] printf[/COLOR][COLOR=#303336]([/COLOR][COLOR=#7D2727]"err: %d\t errno: %d\n"[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] err[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] errno[/COLOR][COLOR=#303336]);
[/COLOR]
```[COLOR=#242729][FONT=Arial][I]
(Full code available on [pastebin]("http://pastebin.com/dpRRq3Aq").)[/I][/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]
I infer the values for the first two arguments of pcm_open from aplay --list-devices, which outputs:
[/FONT][/COLOR]
```
[COLOR=#303336]
**** List of PLAYBACK Hardware Devices ****
card 1: PCH [HDA Intel PCH], device 0: ALC3232 Analog [ALC3232 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]
```[COLOR=#303336]
[/COLOR]

---

