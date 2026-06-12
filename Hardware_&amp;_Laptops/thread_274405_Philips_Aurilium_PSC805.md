---
title: "Philips Aurilium PSC805"
date: 2006-10-09
forum: Hardware &amp; Laptops
---

### Post by ocdude on 2006-10-09
I have a spare Philips Aurilium PSC805 laying around back home (I'm currently not even in the same country as it). I was wondering if anyone had ever used it with Ubuntu. I currently run dapper on my laptop, and am planning on building a machine at the lowest cost possible using stuff I have around.

This soundboard is USB2.0, has 5.1 audio and optical out. On my mac, I was able to get it to somewhat support all the features on the board, but I haven't even tried it on Linux. Anyone?

---

### Post by alan_daniel on 2006-12-20
I just got one of them, and when I plugged it into the machine, it recognized it as a sound device, and the test sounds worked once...still trying to get it working regularly

found anything out yourself?

p.s. - i'm running Edgy

---

### Post by stolid_agnostic on 2007-10-27
> **alan_daniel said:**
> I just got one of them, and when I plugged it into the machine, it recognized it as a sound device, and the test sounds worked once...still trying to get it working regularly

found anything out yourself?

p.s. - i'm running Edgy


I also have one of these and although I can control the volume with no problem, the sound goes through the primary soundcard rather than through the usb soundcard. I am imagining that it's a matter of deciding on a sound device. anyone have thoughts on that?

p.s. - gutsy here

---

### Post by loboc on 2007-11-05
I have been hacking around with mine in Gutsy by configuring  ~.asoundrc i got aplay to play a wav file for the various outputs and amarok to lay mp3s  but haven't tried it with a surround sound source like a dvd yet.

First I dumped the results of alasconf to a file

```
 alsactl -f ~/asound.test names
```

this gave  me a text file with all the defined alsa pcms and ctls the important part is the device aliases.
You can get these aliases with 

```
aplay -L
```

which gives:

```

default:CARD=PCI
    ESS Maestro3 PCI, Maestro3
    Default Audio Device
front:CARD=PCI,DEV=0
    ESS Maestro3 PCI, Maestro3
    Front speakers
null
    Discard all samples (playback) or generate zero samples (capture)
default:CARD=PSC805
    Philips PSC805, USB Audio
    Default Audio Device
front:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    Front speakers
surround40:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=PSC805,DEV=0
    Philips PSC805, USB Audio
    IEC958 (S/PDIF) Digital Audio Output

```

These aliases are incomplete and if you look in that text file we dumped you can see how alsa actual refers to them here is a snippet of the file.  
```

alsactl16 {
                name plug:surround51:1
                comment 'Abstract Device With Conversions - Front, Rear, Center$
        }

```

So for example if we want to refer to the default 2 channel device on the Phillips card we can use the standard alsa hardware identifier you may have seen on alsa howtos  "hw:1,0" is the stereo channel on the card and is what streams are sent to if you just use it as a usb audio device.  the headphones work and stereo will come out of the front channel on the back of the card. 

But the Aurillium has all those other sweet channels on the back. 

The key thing is that little :1 which isnt in the results of aplay -L 

 If we try to play a wav file using aplay it  plays on the laptop speakers.

```

aplay foo.wav
Playing WAVE 'foo.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

 to select another device specify with -D

```

aplay -D "plughw:1,0" foo.wav

```

Plays the wav on card 1 device 0 which should be your Aurilium card.

For all the the other aliases use the name and then :1 to identify on what card the alias is

```

aplay -D surround51:1 gfcool.wav
Playing WAVE 'gfcool.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo
Warning: rate is not accurate (requested = 44100Hz, got = 48000Hz)
         please, try the plug plugin

```


Thats all well and good but aplay isnt going to play your mp3s.
To use those create a ~/.asound.rc file and create easy to remeber aliases for xine and amarok or whatever.
my .asound.rc file  is set up to declare the laptop built in card then the regular old usb-audio stereo
then the digital out on the aurillium and finally the 5.1 surround channel on the aurillium then you can use these aliases in amarok or xine. Not to sure about how to get gnome stuff like banshee and totem-gstreamer to use them.




```


pcm.laptop {
        type plug
        slave.pcm "hw:0"
}

ctl.laptop {
        type hw
        card 0
}

pcm.usb-audio {
        type plug
        slave.pcm "hw:1"
}

ctl.usb-audio {
        type hw
        card 1
}

pcm.usb-digital {
        type plug
        slave.pcm spdif:1
}

ctl.usb-digital {
        type hw
        card 1
}

pcm.usb-51 {
        type plug
        slave.pcm surround51:1
}

ctl.usb-51 {
        type hw
        card 1
}


```

Now for example usb-digtial can be used as a device

```

aplay -D usb-digital gfcool.wav
Playing WAVE 'gfcool.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Stereo

```

Anyway I hope that helps you aurillium using peeps out there.  Ill post more as i discover it.

---

### Post by loboc on 2007-11-06
* Why do I always shout first? Just gives them a chance to run away. Well, I'm an idiot*

So i had a chance to try out that asoundrc file with a toslink cable and a stereo and I failed to produce any sound on the stereo.  aplay not throwing an error was not the indication of success I assumed it to be. Nothing was broken in that it still played sound on the stereo channels.

Any thoughts on getting the pcm subdevices listed by aplay -L to behave in a similar fashion to the subdevices listed by aplay -l?

---

