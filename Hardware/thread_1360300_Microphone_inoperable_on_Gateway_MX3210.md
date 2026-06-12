---
title: "Microphone inoperable on Gateway MX3210"
date: 2009-12-20
forum: Hardware
---

### Post by MontoyaF1 on 2009-12-20
I have a Gateway MX3210 laptop running Ubuntu 9.04 and the sound works, but the microphone jack doesn't.  The problem isn't limited to Skype.  I wanted to be sure that one of my settings are correct.  I have the following checked in the Volume Control Preferences:

Master
Headphone
PCM
Line-in
Microphone
IE958 Playback AC97-SPSA
PC Speaker
External Amplifier
Mic Select

Under the "Options" tab of Volume Control I tried both Mic1 and Mic2 and neither worked.  Are my settings correct?

Thanks!

---

### Post by RedSingularity on 2009-12-20
In a terminal type "alsamixer" and tab over to the "capture" option.  Make sure its all the way up.

---

### Post by MontoyaF1 on 2009-12-22
Thanks for the reply.  I turned it up to 100 as you suggested, but the microphone still doesn't seem to work.  (by the way, I am testing it by using the Sound Recorder utility).

---

### Post by RedSingularity on 2009-12-22
Have pulseaudio installed?

---

### Post by MontoyaF1 on 2009-12-31
No, I don't have any PulseAudio software installed.  Should I download it?

---

### Post by RedSingularity on 2009-12-31
sudo apt-get install pulseaudio

---

### Post by MontoyaF1 on 2010-01-08
> sudo apt-get install pulseaudio
 
You guys are awesome.  That took care of it.  Thanks!!!!

---

### Post by RedSingularity on 2010-01-08
Glad you got it :)

---

