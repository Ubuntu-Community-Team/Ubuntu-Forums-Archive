---
title: "Clevo P170HM/Sager NP8170 subwoofer no output"
date: 2011-12-17
forum: Hardware
---

### Post by madengineer on 2011-12-17
I'm running 11.10 on a Sager NP8170 (Clevo P170HM) and I can't get the subwoofer to do anything. The sound chip is a Realtek ALC892, controlled by snd_hda_intel.

From what I can tell, the problem in a situation like this is usually that snd_hda_intel doesn't know which DAC channel corresponds to which physical audio channel, and this correspondence is controlled by the model= option passed to snd_hda_intel. I've tried no option and model=ref so far, but no joy. I'm testing by running
```
pasuspender -- speaker-test -Dplug:surround51 -c6
```
It produces pink noise from the left and right speakers, but nothing on the LFE.

I don't know where to go from here. There seem to be a bunch of different possible values for model=, but none that are indicated for my particular model of computer, and it looks like I need to reboot to try each new one;
```
modprobe -r snd_hda_intel
rmmod snd_hda_intel
alsa force-reload
``` all fail with the error that the module is in use, even if I run ```
pasuspender -- sleep 100
``` in a different terminal. The only thing I can think of is to start poking around in the source code for snd_hda_intel and try to build a version that tries all the available DAC channels, then with the resulting information come up with a new model= value. It seems like there must be an easier way though.

aplay -L produces the following:
```
default
    Playback/recording through the PulseAudio sound server
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Digital
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC892 Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=1
    HDA Intel PCH, ALC892 Digital
    Hardware device with all software conversions
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=1
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=2
    HDA NVidia, HDMI 0
    HDMI Audio Output
hdmi:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample mixing device
dmix:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=7
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=8
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=9
    HDA NVidia, HDMI 0
    Hardware device with all software conversions
```

---

### Post by bbossola on 2012-08-27
I have exactly the same issue, since one year ago. Sometimes I spend a couple of hours to see anything changed, but nothing happens. There are several issues affecting this, including the fact (for example) that the mic does not switch-off speakers and you need to revert to fn+5 to achieve that, manually :( Also the mic is quite crackling, and the quality of the recorder sound is extermely poor. Difficult to use even skype, in this conditions, which I need for my day work.

In the past, I were able to have the subwoofer (and the res) working installing the drivers from System76 (the Clevo P170HM was shipped as the "bonobo" model from them) with a small hack, but now also that trick does not work anymore, as more upgrades in the system did probably not help and System76 is considering this non-strategic, and they'are probably expecting that, by some magic, their fixes will appear in alsa or even in the kernel (details at [http://ubuntuforums.org/showthread.php?t=1829079](http://ubuntuforums.org/showthread.php?t=1829079))

It's very frustrating, also because if I load windows everything works fine (damn) but I cannot really use that *** to write software (I am developer)

The latest info I found are at [http://www.mentby.com/Group/alsa-list/clevo-p170hm-sager-np8170-audio.html](http://www.mentby.com/Group/alsa-list/clevo-p170hm-sager-np8170-audio.html) but it's too far from my Linux knowledge to represent a solution.

Can anybody there help? Am I the only one out there, with you, with this HW?
Cheers,

B.

---

