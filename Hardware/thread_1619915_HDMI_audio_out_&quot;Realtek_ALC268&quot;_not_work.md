---
title: "HDMI audio out &quot;Realtek ALC268&quot; not working"
date: 2010-11-12
forum: Hardware
---

### Post by artemenko on 2010-11-12
Hi all,

Trying to setup a Boxee box on an older laptop (HP dv6880).  I can play sound fine from from the laptop speakers, but I simply cannot get the sound to output via HDMI on the television.

The picture works fine via the NVIDIA GeForce8400m.

I have also installed the Realtek linux driver from here:
[http://218.210.127.131/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://218.210.127.131/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

From all the forum posts, (and at this point I am just guessing), I am trying to install the latest Realtek drivers, mute everything other than the HDMI out in alsamixer, and locate the correct device in audio preferences.

Unfortunately, I'm not sure what to mute/unmute and audio preferences just shows one device "intenal audio" not anything that appears to be my HDMI out.

> 
tv@tv-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC268 Analog [ALC268 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
tv@tv-laptop:~$ 
> 
tv@tv-laptop:~$ aplay -L
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
pulse
    Playback/recording through the PulseAudio sound server
Whelp, that's all I've got.  I'd love any feedback or new things I can try to get this little science project to work.

Thanks!

---

### Post by lidex on 2010-11-12
The ALC268 card is of no consequence if your hdmi output is on the graphics card - is it? It looks like your hdmi is not being recognized. You'll need v. 1.0.23 of alsa. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

