---
title: "Focusrite Scarlett Solo 2nd Generation problem"
date: 2017-06-12
forum: Hardware
---

### Post by batmanmanbat on 2017-06-12
[COLOR=#333333][FONT=&amp]So I plug it direct to the MB bypassing any HUBs. In Sound in Settings I can see...[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Digital Input(S/PDIF)Scarlett Solo USB[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Analog Input Scarlett Solo USB[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Same for Outputs. So it's there.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]However when I type lspci in console, as su, it doesn't show it.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]00:1f.3 Audio device: Intel Corporation Sunrise Point-H HD Audio (rev 31)[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]That's it for audio devices.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]- So my first question is, where is it? If Sound in Settings can see it, why is it not listed as a hardware device?[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Also I don't understand the difference between digital inputs and outputs. I have no digital inputs. A mic input and guitar input. A headphone output and the USB out and phono audio out. So I can understand that it should be digital out for recording, but why is it showing digital in?[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]So I can play sound through the Scarlett solo. Use the volume monitor knob to adjust the sound in and out through the rear audio outs to my speakers using direct monitor switch. I can also playback on my speakers through the PC without the direct monitor on.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I can get a signal through the mic input. Audacity sometimes sees it. Sometimes doesn't. I can use the preference playback to hear live. Sometimes it works, but sometimes not. Also Audacity is crashing sometimes.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]I got this error message once.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Latency Correction setting has caused the recorded audio to be hidden before zero.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]Audacity has brought it back to start at zero.[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]You may have to use the Time Shift Tool (<---> or F5) to drag the track to the right place.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]So I can't get the stability I need from Audacity to record. Technically I don't need Audacity. Just some recording software.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Qjack doesn't detect the Scarlett at all. [/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]All I can see is Pulse Audio and under it, System. Nothing in MIDI or ALSA about it. However from Settings the Scarlett can be selected at the interface hw:USB but I still get the same connections as before. No mention of the Scarlett.[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]Any ideas what might be up?


Edit:
**SOLVED:** Got answered by some Linux Musicians [here]("https://linuxmusicians.com/viewtopic.php?f=1&t=17182").

Might help someone else someday.[/FONT][/COLOR]

---

