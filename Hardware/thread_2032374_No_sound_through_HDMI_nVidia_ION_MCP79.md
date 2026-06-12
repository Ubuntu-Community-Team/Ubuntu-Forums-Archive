---
title: "No sound through HDMI nVidia ION MCP79"
date: 2012-07-23
forum: Hardware
---

### Post by musicman116 on 2012-07-23
Hey guys.  So, I just installed Ubuntu today on a fairly old mini-PC that I recently acquired.  Everything's working great except for this one thing.  I can't get sound through HDMI.  My graphics processor is an nVidia ION , and when I was looking through alsamixer it said the chipset was MCP79.  I don't really know what else to give you guys right now, I'm fairly new to Linux.  Tell me what stuff I need to get you to help diagnose the problem and I'll do it.

Thank you so much for the help!

---

### Post by papibe on 2012-07-23
Hi musicman116. Welcome to the forums ):P

Could you post the result of the following commands?
```
aplay -l

aplay -L
```
(first -l is a lowercase L).

Regards.

---

### Post by musicman116 on 2012-07-24
Okay, so here's what I get for aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

And here's what I get for aplay -L
```
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=NVidia
    HDA NVidia, ALC888 Analog
    Default Audio Device
front:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Front speakers
surround40:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Digital
    IEC958 (S/PDIF) Digital Audio Output
hdmi:CARD=NVidia,DEV=0
    HDA NVidia, HDMI 0
    HDMI Audio Output
dmix:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct sample mixing device
dmix:CARD=NVidia,DEV=1
    HDA NVidia, ALC888 Digital
    Direct sample mixing device
dmix:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample mixing device
dsnoop:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=1
    HDA NVidia, ALC888 Digital
    Direct sample snooping device
dsnoop:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct sample snooping device
hw:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=1
    HDA NVidia, ALC888 Digital
    Direct hardware device without any conversions
hw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=NVidia,DEV=0
    HDA NVidia, ALC888 Analog
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=1
    HDA NVidia, ALC888 Digital
    Hardware device with all software conversions
plughw:CARD=NVidia,DEV=3
    HDA NVidia, HDMI 0
    Hardware device with all software conversions

```

---

### Post by papibe on 2012-07-24
The Nvidia audio devices are being recognized.

Did you install the Nvidia proprietary driver?

Could you post the result of this command?
```
lspci -nnk | grep -iA2 audio
```
Regards.

---

### Post by musicman116 on 2012-07-25
I'm pretty sure that I installed the latest proprietary drivers.  Here's what that command returns:

```
00:08.0 Audio device [0403]: NVIDIA Corporation MCP79 High Definition Audio [10de:0ac0] (rev b1)
	Subsystem: NVIDIA Corporation Device [10de:a113]
	Kernel driver in use: snd_hda_intel
```

---

### Post by papibe on 2012-07-25
That's look OK.

Let's check if the Nvidia driver is installed and in use.

Could you post the result of this command?
```
apt-cache policy nvidia-current
```
Then could you post the content of this files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```

Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and post back the links.

Regards.

---

### Post by musicman116 on 2012-07-25
Okay, here's what I got back from the terminal command:
```
nvidia-current:
  Installed: 295.40-0ubuntu1
  Candidate: 295.40-0ubuntu1
  Version table:
 *** 295.40-0ubuntu1 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/restricted amd64 Packages
        100 /var/lib/dpkg/status

```

And here's the link to /etc/X11/xorg.conf:

[http://paste.ubuntu.com/1111122/]("http://paste.ubuntu.com/1111122/")

And finally the link for /var/log/Xorg.0.log:

[http://paste.ubuntu.com/1111124/]("http://paste.ubuntu.com/1111124/")

Again, thank you so much for taking the time to look through these and help me out.  I really have no idea what I'm doing when it comes to the inner workings of Linux.

---

### Post by papibe on 2012-07-25
Everything looks good.

I think you should be able to follow this [guide]("http://karuppuswamy.com/wordpress/2012/04/28/how-to-fix-nvidia-hdmi-audio-in-ubuntu-12-04/") and get the sound working.

Tell us how it goes.
Regards.

---

### Post by musicman116 on 2012-07-25
It worked!  For some reason, one of the channels in alsamixer was muted that shouldn't have been.  Thank you so much for your help!

---

### Post by papibe on 2012-07-25
Great :)

Please mark the thread solved (read [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")) when you have the chance.

Regards

---

