---
title: "Intel Bay Trail audio issue"
date: 2017-04-08
forum: Hardware
---

### Post by skerdziuzzz on 2017-04-08
I am using an off-brand chinese laptop with Bay Trail architecture running Lubuntu 16.10. Managed to get audio working in VLC only by installing the 4.11 rc5 kernel and by by downloading files from [https://github.com/plbossart/UCM]("https://github.com/plbossart/UCM") and running ```
sudo cp -rf UCM-master/bytcr-rt5640 /usr/share/alsa/ucm
```Audio works in headphones only at the moment and the stereo channels are reversed.I dont think i can get speakers to work, but is it possible to get audio working for other programs and switching the stereo channels?
aplay -l output ```
**** List of PLAYBACK Hardware Devices ****
card 0: Audio [Intel HDMI/DP LPE Audio], device 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: bytcrrt5640 [bytcr-rt5640], device 0: 1 []
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: bytcrrt5640 [bytcr-rt5640], device 1: Deep-Buffer Audio (*) []
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[IMG]http://i.imgur.com/Jp0oBTP.png[/IMG][IMG]http://i.imgur.com/HbfZ3gA.png[/IMG][IMG]http://i.imgur.com/cvFqZzM.png[/IMG]

Audio only works with bytcr-rt5640 direct hardware device with no software conversions or bytcr-rt5640 hardware device with all software conversions.

[IMG]http://i.imgur.com/CXdspeu.png[/IMG]


EDIT: Installed ubuntu with unity and the gnome sound manager lets me to select the proper device/output thing. Just need to reverse the stereo channels.

---

### Post by TheFu on 2017-04-08
firefox stopped supporting ALSA a few weeks ago. Might be time to switch to Pulse-Audio.  Can't believe I wrote that.  I've been purging pulse from my systems for 5 yrs.

The swapped speakers really sounds like a poor quality control issue - like open up the box and swap the speaker cables.

Might want to specify the CPU, since "bay trail" doesn't help non-nerds (or people that don't do well with code words).  As an example, I'm running 16.04, but couldn't tell you or anyone else what the "code name" is.

---

### Post by skerdziuzzz on 2017-04-08
Well i think its too early to say swapped speakers is a hardware problem since the sound drivers are kind of messed up, in any case it should be possible to swap them by editing alsa or pulse somehow.

Bay Trail is the Intel Atom system on a chip with some kind of intel audio. Also this setup worked for all programs when i used regular ubuntu with unity.

---

