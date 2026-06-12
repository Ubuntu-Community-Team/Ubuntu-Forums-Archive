---
title: "No audio on Ubuntu 18.04 after lot of trials"
date: 2019-06-26
forum: Hardware
---

### Post by zhaodanghan on 2019-06-26
[COLOR=#242729][FONT=Arial]Ubuntu without sound after headphones get unplugged, I have try multiple method seached from Google, but still didn't work out.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I check also with pavucontrol, in output, i find Port: speaker unavailable, I think that the problem come from but I don't know how to deal with it.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Please help me. Thanks at advance.

[https://askubuntu.com/questions/1029502/no-audio-on-ubuntu-18-04](https://askubuntu.com/questions/1029502/no-audio-on-ubuntu-18-04)

[/FONT][/COLOR]

---

### Post by Autodave on 2019-06-26
Please give us some info on your equipment.

---

### Post by zhaodanghan on 2019-06-27
x@x:~$ lspci -v | grep -A7 -i "audio"
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
	Subsystem: CLEVO/KAPOK Computer Device 96e1
	Flags: bus master, fast devsel, latency 32, IRQ 16
	Memory at b461c000 (64-bit, non-prefetchable) [size=16K]
	Memory at b4200000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
--
01:00.1 Audio device: NVIDIA Corporation Device 10f8 (rev a1)
	Subsystem: CLEVO/KAPOK Computer Device 95e1
	Flags: bus master, fast devsel, latency 0, IRQ 17
	Memory at b4000000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel

x@x:~$ aplay -l
**** PLAYBACK &#30828;&#39636;&#35037;&#32622;&#28165;&#21934; ****
card 0: PCH [HDA Intel PCH], device 0: ALC1220 Analog [ALC1220 Analog]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC1220 Digital [ALC1220 Digital]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 9: HDMI 3 [HDMI 3]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 10: HDMI 4 [HDMI 4]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  &#23376;&#35774;&#22791;: 1/1
  &#23376;&#35774;&#22791; #0: subdevice #0

---

### Post by zhaodanghan on 2019-06-27
[COLOR=#000000][INDENT]The problem maybe come from here: in alsamixer i can't increase or decrese the volume of speaker and headphone. [COLOR=#222222]If you need more infos, please let me know. Thanks for your helps.[/COLOR][/INDENT]


[/COLOR]

---

### Post by zhaodanghan on 2019-06-27
The problem maybe come from here: in alsamixer i can't increase or decrese the volume of speaker and headphone.

---

### Post by him610 on 2019-06-27
In alsamixer, if F6 is pressed which audio card is shown as selected? Try selecting the internal one on the motherboard for headphones or speakers connected to rear panel of motherboard. Adjust as appropriate.

---

