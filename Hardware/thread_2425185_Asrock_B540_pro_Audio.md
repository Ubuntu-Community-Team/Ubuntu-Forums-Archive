---
title: "Asrock B540 pro Audio"
date: 2019-08-21
forum: Hardware
---

### Post by coacharnold on 2019-08-21
So I got this great news motherboard cpu combo.  ASROCK b540 pro with a ryzen 3 cpu.  It's a really nice setup.  Kubuntu 19.04 transferes right over like a dream.... Except one thing.  It seems my NVIDIA video card HDMI audio takes over the audio and is the only audio output seen by the system.  All searches only show the graphics cards HDMI  sound out.

From what I can tell I'm disabling the. Realtek áudio By having the graphics card installed.   I can't find anything in the bios that fixes this ..i have tried to install Realtek Linux drivers with no success...Does anyone have experience with this?

---

### Post by him610 on 2019-08-21
> All searches only show the graphics cards HDMI sound out.
How did you conduct all of your searches? Please show each command and its results within the code tags.
Each device with an audio chip in your system should be detectable. You may have a configuration issue. Do you have headphones or speakers connected to your system?

---

### Post by lammert-nijhof on 2019-08-22
I had the same type of problem, but I had no sound at all. I installed PulseAudio Volume Control and it displayed two audio controllers and I declared the HDMI audio off-line in the configuration tab. 
I have done the same with my current Ryzen 3 2200G with an Asrock B450 HDV Rel 4 motherboard. I have again two audio controllers displayed, but now both with the same name and I off-lined the upper one, the one related to HDMI of my Vega-8 Integrated Graphics.
Off line the HDMI one and reboot and see whether the other Realtek appears in the process.

---

### Post by coacharnold on 2019-08-22
lspci  - gets me this 

10:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 8400 GS Rev. 3] (rev a2)
10:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

aplay - l 

desktop:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


lsmod | grep snd - gets this 


fausto@fausto-desktop:/etc$ lsmod | grep snd
snd_hda_codec_hdmi     53248  4
snd_hda_intel          40960  1
snd_hda_codec         131072  2 snd_hda_codec_hdmi,snd_hda_intel
snd_usb_audio         233472  2
snd_hda_core           86016  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_usbmidi_lib        36864  1 snd_usb_audio
snd_hwdep              20480  2 snd_usb_audio,snd_hda_codec
snd_pcm               102400  5 snd_hda_codec_hdmi,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hda_core
snd_seq_midi           20480  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            36864  2 snd_seq_midi,snd_usbmidi_lib
snd_seq                69632  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              36864  2 snd_seq,snd_pcm
snd                    81920  17 snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_usb_audio,snd_usbmidi_lib,snd_hda_codec,snd_timer,snd_pcm,snd_rawmid


and 

cat /proc/asound/cards

 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xf7080000 irq 65

---

