---
title: "Audio does not switch to USB headset on connection"
date: 2016-11-04
forum: Hardware
---

### Post by sorceror171 on 2016-11-04
I've been using analog speakers and analog headphones (via a simple splitter plugged into the sound card sound port) for a long time now. When I want speakers, I turn them on, otherwise off. This has worked fine for quite a while, but the kids have started running chairs over the headphone cords. I'm looking into USB headsets and such. I've got a couple to different headsets to try, but there's an issue.

Loading the pulseaudio module "module-switch-on-connect" is supposed to direct streams to a new device when you plug it in. This is not working, at all. I've confirmed via "pacmd list-modules" that it's loaded, but the *only* way I can get sound to go out of the USB headset is to open up pavucontrol, go to the "Configuration" tab, and turn off "Built-in Audio" completely. At that point, streams switch over. Turning "Built-in Audio" back on switches the streams back. Note that unplugging the USB headset *doesn't* switch back - I *must* turn the Built-in Audio back on to "Analog Stereo Duplex" to hear the streams again. At least sound-producing apps don't crash...

Does anyone have this working? Is there some configuration detail I'm missing?

System: Xubuntu 16.04, internal sound Intel "6 Series/C200 Series Chipset Family High Definition Audio Controller". (There's also a "GM204 High Definition Audio Controller" from the Nvidia card, but that's permanently set to "Off" in pavucontrol.)

USB headsets tried: Plantronics C520-M, Turtle Beach  PX3.

---

### Post by sorceror171 on 2016-11-06
I never did get "module-switch-on-connect" to work, but I've come up with what appears to be a workable workaround. I've set up "module-combine-sink" to send streams to both the USB headset and the motherboard audio at the same time. I can now just turn the speakers on only when I want external sound. Based on the information [here]("http://www.deseret-tech.com/journal/pulseaudio-combine-sinks-for-simultaneous-output/"), I added the following line to /etc/pulse/default.pa:

```
load-module module-combine-sink sink_name=combined slaves=alsa_output.pci-0000_00_1b.0.analog-stereo,alsa_output.usb-Turtle_Beach_Turtle_Beach_PX3__PC_-00.iec958-stereo
```

This caused a loss of functionality, though... only the volume controls in pavucontrol worked. The volume control on the USB headset, and the volume buttons on my keyboard, no longer did anything. I'm using Xubuntu, so following the directions [here]("https://wiki.archlinux.org/index.php/PulseAudio#Keyboard_volume_control"), I added commands to the Application Shortcuts in the Settings->Keyboard control panel. For muting, I used:

```
pactl set-sink-mute @DEFAULT_SINK@ toggle
```

And for volume up, I used:

```
sh -c "pactl set-sink-mute @DEFAULT_SINK@ false ; pactl set-sink-volume @DEFAULT_SINK@ +5%"
```

(Volume down is, presumably, obvious.) At this point I have the desired behavior, and both the keyboard and on-headset volume controls work.

---

