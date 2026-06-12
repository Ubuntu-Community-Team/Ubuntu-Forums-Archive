---
title: "HDMI audio output problem"
date: 2016-01-31
forum: Hardware
---

### Post by marko24 on 2016-01-31
Hi guys, I have been using Xubuntu for a month now and enjoyed very much in every aspect of user experience and functionality untill I ran to a huge problem around a week ago... when connecting my Laptop via HDMI to my PHILIPS Smart TV I cannot manage to get sound working...

My hardware: 
ASUS N76V
Intel core i7
Nvidia Geforce GT650M
16GB DDR3 RAM

I have latest nvidia drivers installed and latest alsa daily driver packages but for some reason I don't get the HDMI sound output option in alsamixer or in pavucontrol

When I type aplay -l in terminal i get following devices (HDMI cable is on):
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC663 Analog [ALC663 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 1: ALC663 Digital [ALC663 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

When I try to change sound card in alsamixer here are the options that I get:
- (default)
0 HDA Intel PCH
enter device name...

Options that I get in pavucontrol:
Built-in Audio:
Analog Stereo Duplex
Analog Stereo Output
Digital Stereo (IEC958) Output + Analog Stereo Input
Digital Stereo (IEC958) Output
Analog Surround 2.1 Output + Analog Stereo Input
Analog Surround 2.1 Output
Analog Surround 4.0 Output + Analog Stereo Input
Analog Surround 4.0 Output
Analog Stereo Input
Off

I have tried multiple "solutions" related to correctly installing sound drivers and configuring settings but none worked for me.
It seems that OS is unable to create or detect HDMI virtual sound card.

This is not in any way hardware related! (It works in Windows).

I hope that someone can help me save my time and nerves since I have been searching for solutions for the whole week on forums and none worked for me. I really wouldn't like to switch back to windows but the problem is quite significant for me since my laptop speakers are pretty bad and I cannot sacrifice OS feature that big. Thank you all in advance!

---

### Post by Vladlenin5000 on 2016-01-31
Hi and welcome.

What nvidia drivers version you have exactly? How did you installed it?

---

### Post by grahammechanical on 2016-01-31
Which version of Xubuntu are you using? I do not know how to do it Xubuntu but for about a year now I have been able to open Sound Settings and in the output tab select HDMI/DisplayPort2 GT216 HDMI Audio Controller as the output.

GT216 is the Nvidia graphic adapter and I am using a HDMI connection to a Sharp TV and getting sound out of the TV speakers. I could do this in 15.10 and I am now using 16.04 development branch and I can still this.

I have also found with the upgraded sound settings that appeared about a year ago that it has a kind of plug & play feature. Plug in headphones and they appear as an output option. Plug in a microphone and it appears as an input option. The devices do not appear as options until they are plugged in.

Regards.

---

### Post by marko24 on 2016-02-01
Currently I am using the proprietary driver nvidia-352 (an option that came preinstalled on xubuntu), but I have already installed multiple versions of graphic drivers and none fixed the problem (however some of them failed to boot into xfce after installing them so had to remove them through shell).

I am on Xubuntu 14.04 stable and when I plug in the TV I do not get virtual HDMI sound card...

UPDATE: When I set my output on pavucontrol to digital stereo, unmute S/PDIF in alsamixer and play a video in youtube I manage to "see sound coming from firefox" in the pavucontrol's  playback settings, however still no sound comes out of TV... I believe that it has to be either driver related (but it is getting frustrating since I tried with both multiple alsa drivers and nvidia drivers already) or it could be a bug.

---

