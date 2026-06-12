---
title: "Audio not working properly"
date: 2009-09-08
forum: Hardware
---

### Post by manolomanolo on 2009-09-08
Hi.

Suddenly my Ubuntu 9.04 box is unable to reproduce audio properly. No recent updates could have affected. I mean no updates at all during the previous two days before the problem presented, as far as I can remember. Also, recent updates have not been audio related, as far as I know. Actually I cannot remember I got recent audio related updates.

I can hear just a tiny distorted noise instead of:
[LIST]
[*]ubuntu startup noise
[*]mp3 playing from my hard drive
[*]audio from youtube
[*]emesene sounds
[*]etc
[/LIST]

The only rare cases in which I can hear clear sounds are:
[LIST]
[*]***System*** -> ***Preference*** -> ***Sound*** and press on "test" buttons when **HDA Intel Alc268 Analog (OSS)** is selected (STRANGE: I have got two identical items named **HDA Intel Alc268 Analog (OSS)** in the list of *Sound Events*, *Music and Movies*, *Audio Conferencing*... could it be the problem?!?)
[*]passing the mouse over an mp3 file starts a correct audio preview, while opening it with VLC causes the tiny distorted sound as above
[/LIST]

Any suggestion please? Thanks.

```
lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

Acer Aspire 5730z - Ubuntu 9.04
alsa-base 1.0.18.dfsg-1ubuntu8
pulseaudio 1:0.9.14-0ubuntu20.2
Kernel 2.6.28-15-generic #49-Ubuntu SMP

**[COLOR="Red"]*** UPDATE 1 ***[/COLOR]**
**Totem**, **Banshee**, **Rythmbox** work perfectly
**VLC**, **Audacity**, **Mplayer Video** stopped working.
It could be interesting to know which (different?) audio module is used by the first (working) and the second (not working) group. I've been trying to take a look at ***System Monitor*** to discover it through observing CPU percentage usage of any audio module (such as alsa or pulse) while executing each of those programs but I had no luck.

**[COLOR="Red"]*** UPDATE 2 ***[/COLOR]**
I reinstalled all gstreamer packages from Synaptic and restarted Ubuntu but that didn't solved the problem.

At the moment the problem is that selecting AUTODETECT or **Pulseaudio Sound Server** from
*System* -> *Preferences* -> *Sound*
will produce the sound problem as described above when pressing the TEST button. Otherwise, selecting **HDA Intel Alc268 Analog (ALSA)** will show this error message:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

while selecting **OSS Open Sound Server** gives:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```

At the moment some examples of working programs are:
Banshee, Totem Movie Player, VLC, I can hear a perfect audio preview, Avidemux (after selecting OSS from its preferences), Kino.

On the other hand the examples of non working are:
Audacity, can't hear sound from Youtube videos or MySpace audio player (I used both Firefox and Chromium), Gmerlin Player (neither selectiog OSS, ALSA, Jack nor EsounD output plugins)

**[COLOR="Red"]*** UPDATE 3 ***[/COLOR]**
Audio works perfectly running Ubuntu 9.04 from live CD on my laptop.
Selecting AUTODETECT in *System* -> *Preferences* -> *Sound* produces good TEST sound.

**[COLOR="Red"]*** UPDATE 4 ***[/COLOR]**
[B][COLOR="Navy"]SOLVED :guitar:

I installed the latest alsa drivers following this guide:
[http://monespaceperso.org/blog-en/?p=225&cpage=1]("http://monespaceperso.org/blog-en/?p=225&cpage=1")

The only "problem" is that maximum volume is lower than when my audio worked properly, even if all the levels are at top in alsamixer.[/COLOR][/B]

---

### Post by manolomanolo on 2009-09-08
I updated the post of above. Thanks for your attention.

---

### Post by Yellow Pasque on 2009-09-08
All the 'working' programs (Rbox, Totem, Banshee) use gstreamer, so they will use whatever gstreamer backend you have selected in System -> Preferences -> Sound.

---

### Post by manolomanolo on 2009-09-09
Thanks for your reply.
Unfortunately I'm not sure I understood whether you are recommending me to use a particular option or sound driver or not. Anyway, inspired by your post, I reinstalled all gstreamer packages from Synaptic and restarted Ubuntu but that didn't solved the problem.

At the moment the problem is that selecting AUTODETECT or **Pulseaudio Sound Server** from
*System* -> *Preferences* -> *Sound*
will produce the sound problem as described above when pressing the TEST button. Otherwise, selecting **HDA Intel Alc268 Analog (ALSA)** will show this error message:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```

while selecting **OSS Open Sound Server** gives:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback. Device is being used by another application.
```

At the moment some examples of working programs are:
Banshee, Totem Movie Player, VLC, I can hear a perfect audio preview, Avidemux (after selecting OSS from its preferences), Kino.

On the other hand the examples of non working are:
Audacity, can't hear sound from Youtube videos or MySpace audio player (I used both Firefox and Chromium), Gmerlin Player (neither selectiog OSS, ALSA, Jack nor EsounD output plugins)

---

### Post by manolomanolo on 2009-09-09
Audio works perfectly running Ubuntu 9.04 from live CD on my laptop.
Selecting AUTODETECT in *System* -> *Preferences* -> *Sound* produces good TEST sound.

---

### Post by manolomanolo on 2009-09-09
SOLVED :guitar:

I installed the latest alsa drivers following this guide:
[http://monespaceperso.org/blog-en/?p=225&cpage=1]("http://monespaceperso.org/blog-en/?p=225&cpage=1")

The only "problem" is that maximum volume is lower than when my audio worked properly, even if all the levels are at top in alsamixer.

---

### Post by cml21 on 2009-09-10
Thanks!  I had the same problem, and this fixed it!

-CML

---

