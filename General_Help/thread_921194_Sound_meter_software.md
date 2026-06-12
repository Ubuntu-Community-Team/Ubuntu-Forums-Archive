---
title: "Sound meter software"
date: 2008-09-16
forum: General Help
---

### Post by morque on 2008-09-16
does anyone know of any software where I could use the microphone on my computer and get a sound level readout like in dB or something?  I realize that using my poor quality microphone probably wont  be very accurate, but I just want a quick and dirty way to just get a readout of the volume level and I dont really have the time/ money to go buy one of the professional units that are available commercially.  I am even willing to use windows based software if you know of any thats free.

---

### Post by ryanhaigh on 2008-09-16
I don't know of anything specifically for measuring the sound level but you can probably use [apt://audacity]("apt://audacity") to do what you want.

Arecord is a very simple command line utility that has a simple volume meter when use in verbose mode:
```

arecord -Dhw:0 -c2 -fS16_LE -r48000 /dev/null -vv

```

If you are using Hardy which comes with pulseaudio there is an application called pavumeter:
> 
PulseAudio Volume Meter

PulseAudio, previously known as Polypaudio, is a sound server for POSIX and WIN32 systems. It is a drop in replacement for the ESD sound server with much better latency, mixing/re-sampling quality and overall architecture.

A simple GTK volume meter for the PulseAudio sound server. 

Searching for volume meter in synaptic might find you other tools as well.

---

### Post by Kociubinska on 2008-10-24
I like this site:
[http://www.darkwood.demon.co.uk/PC/meter.html](http://www.darkwood.demon.co.uk/PC/meter.html)

---

