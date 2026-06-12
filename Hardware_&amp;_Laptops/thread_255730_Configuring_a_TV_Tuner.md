---
title: "Configuring a TV Tuner"
date: 2006-09-11
forum: Hardware &amp; Laptops
---

### Post by scratched on 2006-09-11
I recently purchased a Sabrent TV-PCB05 PCMCIA TV tuner for my laptop. The card is recognized and the light on the card comes on, but it doesn't work yet. I found a post from someone with [the exact same card explaining how he got it to work]("http://ubuntuforums.org/showthread.php?t=172085") but I can't figure out what I need based on his HOWTO. 

The main thing on his HOWTO is how the driver module should be loaded. It says the module should load with the options "card=79 tuner=54". What do I need to do to make the driver load that way?

I'm a relative newbie when it comes to configuring hardware so I'm pretty clueless.

Also, the website I bought it from advertises this item as a TV-PCB01. The label on the tuner says TV-PCB05, but from looking at pictures on several websites they appear to be identical in everything except name.

---

### Post by Dogmeat on 2006-09-12
You have to find out first which module your card uses.
The most common modules I guess are bttv and saa7134, so try these commands:

```
lsmod | grep bttv
```
```
lsmod | grep saa7134
```

If you get anything other than a blank line, you found the module your card is using. Let's assume it's bttv.

You now have to edit a file so the module will load with these parameters everytime you boot the system. This file is /etc/modprobe.d/options

Type:

```
sudo gedit /etc/modprobe.d/options
```

Then add a this line at the end of the file and save it:

```
options bttv card=79 tuner=54
```

Don't forget to replace bttv with your module, if it's not bttv.
Restart your computer and try to watch TV with tvtime for example. It's a very good program and it's on synaptic.

---

### Post by scratched on 2006-09-12
That worked great. Now my card works even better than in windows! Thanks!

I still haven't tried cable or the radio but my N64 works great now:D 

For anyone who may come across this thread in the future, you need to use this shell script written by Beartard to run tvtime with sound:
```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute
```

---

### Post by KeyExpert on 2006-12-29
After following the instructions above to a "t," I still can't get sound to work in tvtime or kdetv.  When I run the provided script, I hear only a repetitive click, much like one would hear at the end of a record as the needle jumps continuously over the final groove.  As I am a complete linux and ubuntu n00b, I'm really at a loss as to where to go from here to even begin troubleshooting the problem.  So I pose the question to you fine folks.

I've searched the web and ubuntu forums extensively trying to find any information at all relating to the PCB-05 tuner and so far this is the only thread I've found.  Help me get my sound!!!

](*,)

---

### Post by acce245 on 2007-12-30
After thoroughly searching through google with search criteria of 'what is ossdsp' I came across something, and decided to try it.  This is not really to my credit, although it now works for me.  Perhaps you will find it equally useful.

[PHP]
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute[/PHP]


Let me know how that works out for you.  I simply saved it as a text file on my desktop, and then copy and paste.

That actually only works for me part of time.

I am trying this too

[PHP]#!/bin/sh
sox -r 32000 -w -t ossdsp /dev/dsp2 -t ossdsp /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute[/PHP]

Let me know if it works, or any other fixes.  Audio is choppy.... I am not a programmer, so I am just playing around with the code given.

Can someone explain the other parts -r -s and so forth?  I am a newbie and need help!

Also, on the latter, by changing 32000 to 16000 and 8000, I get much better performance, and no chop.

---

### Post by acce245 on 2007-12-30
One other simple way I found to get audio to sync close at 32000 and 16000 (less than .5 second delay) was to use vlc.  Simplest way is to do this:

Start TVTime before starting VLC

install vlc
open vlc
click file
click Open Capture Device
type 2 behind /dev/dsp in the audio
click advanced options
type 32000 or 16000 into samplerate
click OK and OK again

This should do it.  

If someone could write a script for simply opening TVTuner and VLC and doing this, that would be great.  I think this will solve a lot of headaches for people in the near future!

---

### Post by acce245 on 2007-12-30
bump

---

### Post by acce245 on 2007-12-30
Or, the simplest way I have found, is to use tv tuner to select channel, exit tv tuner, open terminal and copy and paste this in:
[PHP]
vlc v4l:// :v4l-vdev="/dev/video0" :v4l-adev="/dev/dsp2" :v4l-norm=3 :v4l-frequency=-1 :v4l-caching=300 :v4l-chroma="" :v4l-fps=-1.000000 :v4l-samplerate=32000 :v4l-channel=0 :v4l-tuner=-1 :v4l-audio=-1 :v4l-stereo :v4l-width=0 :v4l-height=0 :v4l-brightness=-1 :v4l-colour=-1 :v4l-hue=-1 :v4l-contrast=-1 :no-v4l-mjpeg :v4l-decimation=1 :v4l-quality=100[/PHP]

Hope that is helpful.

more edits as I discover more stuff.

Or, similarly, also put a 1 behind /dev/video on the video chooser in VLC, put a 2 behind /dev/dsp in the audio, and in the advanced settings, put samplerate to 32000.  Also, by running scantv (after install with apt-get), you can get your channel frequency guide, and then just input it (such that if frequency is 12.34 for example, you would type 12340).

Hope that helps.

---

