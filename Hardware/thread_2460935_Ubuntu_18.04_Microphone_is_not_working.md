---
title: "Ubuntu 18.04 Microphone is not working"
date: 2021-04-21
forum: Hardware
---

### Post by bogoyette on 2021-04-21
Ubuntu 18.04 
Microsoft Teams Version 1.3.00.16851 (64 bit).
                 Microphone is not working in Teams meetings but always works when [[COLOR=#000000]taking mic test[/COLOR]]("https://mictests.net") online.
Microphone is working in all other Apps: Skype, Zoom, sound recording, etc...
Tried USB, Bluetooth and direct connect mics with same result.
                 Microphone seems to work in Teams meetings if I start Teams with SUDO. 
Permission problems? Why does mic work when doing a test call?
Seems  to me that the &amp;amp;#34;Test call&amp;amp;#34; function  code copied into Teams APP from Skype (Mic with Skype always works)

---

### Post by annajane on 2021-04-23
[COLOR=#212529][FONT=-apple-system]I am running Ubuntu 18.04.4 on a Lenovo ThinkPad T400. I have been using the microphone **in the past without problems** with applications such as Google Hangouts, Skype, … – Recently, I tried to have a call and noticed that the microphone **stopped working**. Speakers are fine. I cannot tell how long the microphone misfunctions or if it stopped working with a software update or such.[/FONT][/COLOR]
[h=1]What I tried[/h]
[LIST=1]
[*]I checked *System Settings / Sound / Input* – there is nothing muted and the input level does not recognize any sound.
[[IMG]https://i.stack.imgur.com/RteI6.png[/IMG]]("https://i.stack.imgur.com/RteI6.png")

[*]I checked alsamixer but could not find anything unusual. Here a screenshot where the internal microphone is selected (last column, red).
[[IMG]https://i.stack.imgur.com/AbpuJ.png[/IMG]]("https://i.stack.imgur.com/AbpuJ.png")

[*]I checked puvacontrol. Nothing suspicious there.
[[IMG]https://i.stack.imgur.com/HCvdd.png[/IMG]]("https://i.stack.imgur.com/HCvdd.png")

[*]I tried sudo alsa force-reload and the rebooting. No success.

[*]I tried reinstalling alsa-base and pulseaudio:
sudo apt-get remove alsa-base pulseaudio  
sudo apt-get install alsa-base pulseaudio  
sudo alsa force-reload
Rebooting after. Microphone is still not working.

[*]When I plug in an **external microphone** then the input level in *System Settings / Sound / Input* does **successfully** recognize the sound.

[*]I let the pulse configuration to be created freshly:
mv ~/.config/pulse/ ~/.config/pulse.BAK
Rebooting after. Microphone is still not working.
[/LIST]

---

