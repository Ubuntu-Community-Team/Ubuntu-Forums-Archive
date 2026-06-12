---
title: "HDMI Audio"
date: 2009-07-24
forum: Hardware
---

### Post by Moth Dust on 2009-07-24
Hello, This is my first post, sorry it's already been discussed so much :(. Basically I've been lurking around these forums and other forums and websites for an answer for about 3 days now, putting in maybe 6 hours of work each day and I can't figure this out. I have an HP notebook dv9700 and have video out for HDMI but audio from laptop speakers, would like audio out HDMI to TV.

I am going with ALSA since that seemed to be what everyone else was doing, this disables my ability to adjust volume with the touchpad on my laptop, but beggers can't be choosers. All I'm saying is if pulse would be easier than feel free to let me know since I can't really claim to know the differences between them.

aplay -l gives me


**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L gives me

front:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC268 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

and cat /proc/asound/devices gives me

 0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  5: [ 0- 1]: hardware dependent
 16: [ 0- 0]: digital audio playback
 22: [ 0- 6]: digital audio playback
 24: [ 0- 0]: digital audio capture
 30: [ 0- 6]: digital audio capture
 33:        : timer

Now when I tried to test 0,6 with a wav file I got an error. But being kind of a noob in Linux not sure if that matters or not, pretty sure my list would say HDMI if it was recognizing it at all. I also assumed it would be an NVIDIA device and not Intel but I'm not too familiar with troubleshooting audio problems.

I'd like to thank you guys and girls in advance, my time lurking has shown me this is a very mature forum. Hope I'm not being a pest >.<!!



Made thread in wrong section of the forums! sorry, made new thread in correct section, Don't know how to Delete this thread, sorry :(.

---

