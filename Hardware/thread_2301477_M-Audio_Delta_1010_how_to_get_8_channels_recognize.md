---
title: "M-Audio Delta 1010 how to get 8 channels recognized by Pulse Audio"
date: 2015-11-02
forum: Hardware
---

### Post by mike4ubuntu on 2015-11-02
does anybody know how to get Pulse Audio, specifically pavucontrol, to recognize the 8 output and 8 input channels of the M-Audio Delta 1010?  I've installed mudita24 which gives you a good patchbay for the device and all of the channels, but that doesn't help Pulse audio recognize the channels.  I tried the suggestion of editing the  /etc/pulse/default.pa file with the following (have to replace M1010LT with the name that shows up for specific variant of the Delta 1010:

```

load-module module-alsa-sink sink_name=M1010LT_Analog_Out device=hw:M1010LT channels=10 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7

load-module module-alsa-source source_name=M1010LT_Analog_In device=hw:M1010LT channels=12 channel_map=left,right,aux0,aux1,aux2,aux3,aux4,aux5,aux6,aux7,aux8,aux9

(this is two lines).

Also comment out the udev section (~7 lines) starting "### Automatically load driver modules depending on ...". 

Then run "pulseaudio --kill && pulseaudio --start", and you should be done.

```

However, that disabled all of my other sound interfaces.  Does anybody have any experience with this sound card?

---

### Post by mike4ubuntu on 2015-11-05
bump

not much going on here so far.  Is anybody using this sound card anymore?  Some reports say you can create a ~/.asoundrc file with alsa config in it to get the additional channels, but I haven't been able to figure out the right content of this file.  I used these web pages for info on the syntax of the .asoundrc file.  Any help is much appreciated.

Alsa support

[http://www.alsa-project.org/main/index.php/Asoundrc]("http://www.alsa-project.org/main/index.php/Asoundrc")
[http://alsa.opensrc.org/Asoundrc]("http://alsa.opensrc.org/Asoundrc")

---

### Post by tgalati4 on 2015-11-05
I have a Delta66 card, but I've only used it with *audacity* recording and *envy24* (now *mudita24*) to set up patches.  I did not need a special .asound file to get it to work, nor have I used it with *pulseaudio*.  It was a dedicated recording box, not a destkop.

Turn on verbosity and start digging:

```
pulseaudio -vvv
```

I noticed that you have 12 input channels specified.  I thought the Delta1010 card had 10 inputs and 10 outputs.

Do you have all the *pulseaudio* tools loaded?

> padevchooser - PulseAudio Device Chooser
paman - PulseAudio Manager
paprefs - PulseAudio Preferences
pasystray - PulseAudio controller for the system tray
pavucontrol - PulseAudio Volume Control
pavucontrol-dbg - Debugging symbols for pavucontrol
pavumeter - PulseAudio Volume Meter


---

### Post by mike4ubuntu on 2015-11-05
yeah, not sure where I got the extra 2 input aux channels from.  I just copied from somebody's posted config.  I'll try taking them off and see what happens.  Looks like I had all of  tools installed somehow, but I didn't know about a few of them like paprefs and pasystray, so , thanks I 'll give them a try.  I also have mudita24 installed and I can only get sound to go to channels 1-2.  I don't see a way to output to channels 3-10.  Even with the ALSA tools, I don't see a way to output to those channels.

```

$ aplay -l
...
card 2: M1010 [M Audio Delta 1010], device 0: ICE1712 multi [ICE1712 multi]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

$ aplay -L
...
sysdefault:CARD=M1010
    M Audio Delta 1010, ICE1712 multi
    Default Audio Device
front:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    Front speakers
surround40:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    4.0 Surround output to Front and Rear speakers
surround41:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
iec958:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    Direct sample mixing device
dsnoop:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    Direct sample snooping device
hw:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    Direct hardware device without any conversions
plughw:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    Hardware device with all software conversions

```

seems like there should be plughw:CARD=M1010,DEV=0 through plughw:CARD=M1010,DEV=7.

I haven't tried "audacity", but I'll call it up just to see what outputs/inputs it has available.  I was really planning on trying to get jackd and ardour working together if I can get all of the channels available.

---

### Post by tgalati4 on 2015-11-06
Channels will only show up once they are defined and saved as profiles in *mudita24*.  The Delta card channels are matrixed and only exist once patches are made.  They do not have hard input and output channels, but rather software-defined channels unlike a traditional Intel sound chip.  This gives a lot of mixing and monitoring flexibility, but a pain to set up.

Some reading:  [https://community.ardour.org/node/1198](https://community.ardour.org/node/1198)

[https://wiki.archlinux.org/index.php/Envy24control](https://wiki.archlinux.org/index.php/Envy24control)

[http://ubuntuforums.org/showthread.php?t=1675400](http://ubuntuforums.org/showthread.php?t=1675400)

---

### Post by mike4ubuntu on 2015-11-06
I haven't tried setting up profiles in mudita24 yet.  I read the Envy24control doc, but in the Profiles section it says ToDo.  I'll have to experiment with that.  What does your defined profile look like for the Delta 66?  It kind of looks like the profiles only setup things for sample rate and such.  Is there some way of telling mudita24 to enable/disable certain pcm ins/outs?  it appears that only pcm outs/ins channels 1-2 are enabled through the card and ultimately to the break-out box ports.  The delta 1010 has 8 pcm outs/ins, but right now nothing seems to come out of the break-out box ports for those channels 3-8.

---

### Post by mike4ubuntu on 2015-11-06
I did notice that while testing the paprefs I was able to set PulseAudio to use the surround 5.1 setting
```

$ aplay -L
...
surround51:CARD=M1010,DEV=0
    M Audio Delta 1010, ICE1712 multi
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers

```

and that made more channels available, at least I could see the levels changing for the surround channels.

---

### Post by tgalati4 on 2015-11-06
Yes, the documentation is lacking.  My recording machine is stored in a closet, so it would take a while to dig it out and boot it.  The surround5.1 is a profile that uses 6 speakers.  Perhaps research that and see how it is set up.

---

### Post by mike4ubuntu on 2015-11-13
This really appears to be ALSA driver issue.  For the Delta cards (at least the Delta 44 and Delta 1010), the ice1712 driver is used.  I can get the output to surround5.1 working with output going to 6 of the 8 analog out ports, but there is no surround7.1 provided (for all 8 out ports).  Also, the input is limited to a single stereo input.  This driver probably needs to be updated to provide a 8 in/8 out option, but it doesn't right now.  I'll keep digging and posting any updates here.

---

