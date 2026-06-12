---
title: "Dell Latitude 14 Rugged 5404 - No Audio"
date: 2020-03-25
forum: Hardware
---

### Post by snipes420 on 2020-03-25
I installed Ubuntu 19.10 on a Dell Latitude 14 Rugged 5404 Laptop
There is no sound output to the speakers in the live environment or in the installed system. When I plug in Headphones to the headphone jack, the system detects them being connected, it asks me if they are headphones or a headset, and sound comes out of them. When I plug a HDMI cable to my TV, the HDMI audio device appears and is selected as output automatically and does work correctly. The sound does work correctly in the dual booted windows 10 install if I reboot into it.

Here is the details from windows device manger for the audio device
```
Name	Realtek Audio	
Manufacturer	Realtek	
Status	OK	
PNP Device ID	HDAUDIO\FUNC_01&VEN_10EC&DEV_0292&SUBSYS_1028062F&REV_1000\4&1CDD9025&0&0001	
Driver	c:\windows\system32\drivers\rtdvhd64.sys (6.0.1.6105, 2.56 MB (2,686,200 bytes), 2019-03-17 1:48 PM)
```

Here is the audio devices from lspci
```
tech@my-Latitude-14-Rugged-5404:~$ sudo lspci -nn | grep Audio
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 0b)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series HD Audio Controller [8086:9c20] (rev 04)
tech@my-Latitude-14-Rugged-5404:~$ 
```

and kernel messages output
```
tech@my-Latitude-14-Rugged-5404:~$ dmesg | grep snd
[    3.265555] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3226: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    3.265561] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    3.265563] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[    3.265564] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[    3.265568] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[    3.265571] snd_hda_codec_realtek hdaudioC1D0:      Headset Mic=0x1a
[    3.265572] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[    3.287314] snd_hda_intel 0000:00:03.0: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
tech@my-Latitude-14-Rugged-5404:~$
```

screenshot of my audio settings in the settings app. there is no other devices in the drop down to select to try. The audio activity indicator bar shows that there is audio playing because I am playing a youtube video, and the microphone audio activity indicator bar also shows audio being detected by the microphone when there is noise present. The volume is up and not muted in the GUI.
[IMG]https://bayimg.com/10565bebac29e1097d3f2a4ea4857c60acd686a3.jpg[/IMG]

output of lsmod
```
tech@my-Latitude-14-Rugged-5404:~$ sudo lsmod | grep snd
snd_hda_codec_hdmi     61440  1
snd_hda_codec_realtek   118784  1
snd_hda_codec_generic    81920  1 snd_hda_codec_realtek
snd_hda_intel          49152  7
snd_intel_nhlt         20480  1 snd_hda_intel
snd_hda_codec         131072  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec_realtek
snd_hda_core           90112  5 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek
snd_hwdep              20480  1 snd_hda_codec
snd_pcm               106496  6 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
ledtrig_audio          16384  3 snd_hda_codec_generic,snd_hda_codec_realtek,dell_laptop
snd                    90112  23 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd
tech@my-Latitude-14-Rugged-5404:~$ 
```

I found this page and am working through it now.
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure")

Output of alsa-info.sh
[http://alsa-project.org/db/?f=27dd056551530d1fe280f5d7f5017e864f7ec6ff]("http://alsa-project.org/db/?f=27dd056551530d1fe280f5d7f5017e864f7ec6ff")

Can anyone give me a hint how to look further into what might be the problem?

Thanks

---

### Post by Yellow Pasque on 2020-03-25
This is the only lead I could find and it's for a different Latitude model:
[https://www.spinics.net/linux/fedora/alsa-user/msg13304.html](https://www.spinics.net/linux/fedora/alsa-user/msg13304.html)

Maybe try muting headphone volume in alsamixer using 'm' key?
```
alsamixer
```

---

### Post by snipes420 on 2020-03-27
> **Yellow Pasque said:**
> This is the only lead I could find and it's for a different Latitude model:
[https://www.spinics.net/linux/fedora/alsa-user/msg13304.html](https://www.spinics.net/linux/fedora/alsa-user/msg13304.html)

Maybe try muting headphone volume in alsamixer using 'm' key?
```
alsamixer
```

I just took a look in alsamixer, and it appears that the headphone volume is already muted.

[IMG]https://bayimg.com/3b7e3985bc3b84634cce85ec44c3b4766602a8d1.jpg[/IMG]

I tried playing audio with it muted and unmuted, The thread you located looks very promising but I haven't been able to replicate that persons success.

When I first run alsamixer, the HDMI options are shown. I have to press F6 and select card1 to change to the PCH audio device to change its options/volumes.

[IMG]https://bayimg.com/988fd45c92af1e180c35f9cf4e88f530ffc284e9.jpg[/IMG]

It looks like the HDMI is the 'default' card. Could this be the problem? I have not been able to find a command to see what the default card is, or how to change it. The ubuntu settings app only shows a single device that is able to be selected as output.

TY for helping

---

### Post by Yellow Pasque on 2020-03-27
The screenshot looks like your speaker is muted.
> It looks like the HDMI is the 'default' card. Could this be the problem?
I don't think so. You have the correct device selected in pavucontrol.

---

### Post by snipes420 on 2020-03-27
OK I checked and the speaker is unmuted. I must have took that screenshot while it was. I tried toggling all them on and off during testing.

[IMG]https://bayimg.com/fa87e0fd38cdcb5e31ff44c2544ccc0bec0e0601.jpg[/IMG]

pavucontrol everything looks like I would expect it to look. the audio meter is boucing while playing a youtube video with audio in firefox.

[IMG]https://bayimg.com/3b896a29bc52780e274a4e57789b8f582e3e1fa9.jpg[/IMG]

the output device choices in there are 'speakers' and 'headphones (unplugged)'.
I selected headphones and muted it.
then changed it back to speakers and it is unmuted, but still no audio.

[IMG]https://bayimg.com/73a50372aa7d31d66a9dc89af002f7bb186a1b03.jpg[/IMG]

HDMI does not show up in pavucontrol. it is not plugged in so this may be the reason.

---

### Post by Yellow Pasque on 2020-03-28
I'm out of ideas. Sorry.

---

