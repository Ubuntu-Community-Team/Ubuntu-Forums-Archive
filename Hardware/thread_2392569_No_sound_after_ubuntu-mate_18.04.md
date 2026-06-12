---
title: "No sound after ubuntu-mate 18.04"
date: 2018-05-22
forum: Hardware
---

### Post by kaborayyan on 2018-05-22
[COLOR=#1C1C1C][FONT=&amp]Hello there, I have a cheap netbook/laptop that used to have Windows 10. It was very slow so last year I tried to install Ubuntu 16.04 on it like my main laptop. However, wifi, Bluetooth and sound weren't working with Ubuntu 16.04. I tried different methods but all of them failed terribly. I ditched Ubuntu on this netbook and kept the windows again for a year.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]I tried the live usb of 18.04 and voila wifi is perfect. No Bluetooth. No sound but the audio mixer is showing Atom x5-E8000/J3xxx/N3xxx series PCI.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]I think the new kernel is better for recognizing the hardware than 16.04 kernel. This netbook will be very helpful for me if it works.[/FONT][/COLOR]
[COLOR=#1C1C1C][FONT=&amp]I tried the solution posted by linuxium here:
[http://linuxiumcomau.blogspot.com/2017/10/fixing-broken-hdmi-audio.html](http://linuxiumcomau.blogspot.com/2017/10/fixing-broken-hdmi-audio.html)

however I got stuck in one step:
[/FONT][/COLOR]
> **[FONT=courier new]aplay -l[/FONT]****[FONT=courier new]**** List of PLAYBACK Hardware Devices ****[/FONT]**
**[FONT=courier new]card 0: Audio [Intel HDMI/DP LPE Audio], device 0: HdmiLpeAudio [Intel HDMI/DP LPE Audio][/FONT]**
**[FONT=courier new]Subdevices: 1/1[/FONT]**
**[FONT=courier new]Subdevice #0: subdevice #0[/FONT]**
**[FONT=courier new]card 0: Audio [Intel HDMI/DP LPE Audio], device 1: HdmiLpeAudio [Intel HDMI/DP LPE Audio][/FONT]**
**[FONT=courier new]Subdevices: 1/1[/FONT]**
**[FONT=courier new]Subdevice #0: subdevice #0[/FONT]**
**[FONT=courier new]card 0: Audio [Intel HDMI/DP LPE Audio], device 2: HdmiLpeAudio [Intel HDMI/DP LPE Audio][/FONT]**
**[FONT=courier new]Subdevices: 1/1[/FONT]**
**[FONT=courier new]Subdevice #0: subdevice #0[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]aplay -L[/FONT]**
**[FONT=courier new]default[/FONT]**
**[FONT=courier new]Playback/recording through the PulseAudio sound server[/FONT]**
**[FONT=courier new]null[/FONT]**
**[FONT=courier new]Discard all samples (playback) or generate zero samples (capture)[/FONT]**
**[FONT=courier new]pulse[/FONT]**
**[FONT=courier new]PulseAudio Sound Server[/FONT]**
**[FONT=courier new]sysdefault:CARD=Audio[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Default Audio Device[/FONT]**
**[FONT=courier new]dmix:CARD=Audio,DEV=0[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample mixing device[/FONT]**
**[FONT=courier new]dmix:CARD=Audio,DEV=1[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample mixing device[/FONT]**
**[FONT=courier new]dmix:CARD=Audio,DEV=2[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample mixing device[/FONT]**
**[FONT=courier new]dsnoop:CARD=Audio,DEV=0[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample snooping device[/FONT]**
**[FONT=courier new]dsnoop:CARD=Audio,DEV=1[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample snooping device[/FONT]**
**[FONT=courier new]dsnoop:CARD=Audio,DEV=2[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct sample snooping device[/FONT]**
**[FONT=courier new]hw:CARD=Audio,DEV=0[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct hardware device without any conversions[/FONT]**
**[FONT=courier new]hw:CARD=Audio,DEV=1[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct hardware device without any conversions[/FONT]**
**[FONT=courier new]hw:CARD=Audio,DEV=2[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Direct hardware device without any conversions[/FONT]**
**[FONT=courier new]plughw:CARD=Audio,DEV=0[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Hardware device with all software conversions[/FONT]**
**[FONT=courier new]plughw:CARD=Audio,DEV=1[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Hardware device with all software conversions[/FONT]**
**[FONT=courier new]plughw:CARD=Audio,DEV=2[/FONT]**
**[FONT=courier new]Intel HDMI/DP LPE Audio, Intel HDMI/DP LPE Audio[/FONT]**
**[FONT=courier new]Hardware device with all software conversions[/FONT]**
[B][FONT=courier new]
[/FONT][/B]
**[FONT=courier new]aplay usr/share/sounds/alsa/Front_Left.wav[/FONT]**
**[FONT=courier new]usr/share/sounds/alsa/Front_Left.wav: No such file or directory[/FONT]**



although that the _**file exists in the exact directory!!!**_

Any hope to fix the sound
[COLOR=#1C1C1C][FONT=&amp]

[/FONT][/COLOR]

---

