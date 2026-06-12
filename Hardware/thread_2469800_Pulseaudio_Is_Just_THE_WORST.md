---
title: "Pulseaudio Is Just THE WORST"
date: 2021-12-09
forum: Hardware
---

### Post by Mark76 on 2021-12-09
I know I have a soundcard, aplay also knows I have a soundcard

```
 aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 3: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

And more 

```
aplay -L
default
    Playback/recording through the PulseAudio sound server
surround21
    2.1 Surround output to Front and Subwoofer speakers
surround40
    4.0 Surround output to Front and Rear speakers
surround41
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50
    5.0 Surround output to Front, Center and Rear speakers
surround51
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)
samplerate
    Rate Converter Plugin Using Samplerate Library
speexrate
    Rate Converter Plugin Using Speex Resampler
jack
    JACK Audio Connection Kit
oss
    Open Sound System
pulse
    PulseAudio Sound Server
upmix
    Plugin for channel upmix (4,6,8)
vdownmix
    Plugin for channel downmix (stereo) with a simple spacialization
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, Generic Digital
    HDMI Audio Output
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, Generic Digital
    Hardware device with all software conversions
usbstream:CARD=PCH
    HDA Intel PCH
    USB Stream Output

```

But for some reason Pulseaudio cannot detect the analog stereo duplex and I don't understand why.

---

### Post by TheFu on 2021-12-10
Please run the audio troubleshooting script from the Multimedia sub-forum and post the results.
If the hardware is working, [Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864](Https://ubuntuforums.org/showthread.php?t=2462882&p=14040864#post14040864) might be helpful.
```
pactl list short sinks
``` should show a list of output devices (speakers).  The name in the output from that command can be used for any pulse audio command - like pacmd or pactl since you seem to prefer using the CLI interface.

If you like a GUI, use **pavucontrol**. I don't think that is pre-installed in Ubuntu, but it is in the repos and provides more control over where audio comes in and where it goes out on a per-application basis.

---

### Post by Mark76 on 2021-12-10
Result of running command actl list short sinks

```
1	alsa_output.pci-0000_00_1b.0.hdmi-stereo	module-alsa-card.c	s16le 2ch 44100Hz	SUSPENDED
```

I have pavucontrol installed but it only shows HDMI options, all of which are unavailable

---

### Post by TheFu on 2021-12-11
First - correct, accurate, details matter.  Don't make us guess due to misspellings.  Please.

Usually, HDMI audio is controlled by the video card hardware.  Other audio is controlled by drivers for those devices, typically from Intel in recent systems I've seen. Both my Ryzen systems have Intel Audio drivers for non-HDMI audio. Some older systems have Realtek. If pacmd or pactl don't show an expected output, verify the driver is actually loaded, check that the config files (ALSA and Pulse) haven't disabled the specific device and restart the pulse daemon.  That has always worked for me ... er ... the last few years.

Are you going to run the audio troubleshooting script?

---

### Post by Mark76 on 2021-12-11
Misspellings?  What on earth are you talking about?  I can only paste what the terminal gives me.

Is there any way I can just replace pulseaudio with something that actually works?

---

### Post by Yellow Pasque on 2021-12-11
It looks like only your HDMI codec shows up with aplay, so the problem is deeper than pulseaudio. Run alsa info and give the link:
```
sudo alsa-info
```

---

### Post by Mark76 on 2021-12-11
Okie doakie

[http://alsa-project.org/db/?f=512f7f77e3651b0683cafe7b8942695542301602](http://alsa-project.org/db/?f=512f7f77e3651b0683cafe7b8942695542301602)

Hope that helps solve the mystery

---

### Post by Yellow Pasque on 2021-12-11
> **Mark76 said:**
> Hope that helps solve the mystery

No. It doesn't solve it, but it confirms the problem is not pulseuadio. Your analog codec doesn't show up anywhere. Something is messed up in your BIOS, or maybe Windows FastBoot is causing the issue. Sometimes, Windows can leave the audio codec in a state that Linux doesn't like. Maybe try to reset according to procedure here: [https://www.ifixit.com/Wiki/HP_EliteBook_8460p_Troubleshooting#Section_Laptop_Powers_Up_and_Displays_a_Boot_Error](https://www.ifixit.com/Wiki/HP_EliteBook_8460p_Troubleshooting#Section_Laptop_Powers_Up_and_Displays_a_Boot_Error)

Then, boot directly into Linux.

---

