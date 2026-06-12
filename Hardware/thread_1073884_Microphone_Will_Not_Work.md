---
title: "Microphone Will Not Work"
date: 2009-02-18
forum: Hardware
---

### Post by tacantara on 2009-02-18
I've browsed every possible post I could find on this topic, but have not found a solution.  I can't get my microphone to work with Sound Recorder or Skype.  I have audio playback, but my mic (external and built-in) will not work, no matter what I try.  I am operating a Dell XPS M1330 with Ubuntu 8.10 (first time user).  I like the OS (much faster than Windows) but without the ability to use Skype, I will have to revert to Windows.  Can anyone help me?

---

### Post by handy on 2009-02-19
Did you try this thread?

*_[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)_*

Best I can do for you sorry.

---

### Post by mikewu on 2009-02-19
Try this:

Run in a terminal:
alsamixer -V all

scroll over to Mic and turn it down to 0. This is so there is no feedback.

Scroll over to Mic Capt or Capture. Turn this all the way up.

It's worked for me and some other people, so hope this works for you too.

---

### Post by tacantara on 2009-02-19
mikewu:  Thanks for guiding me back to the Terminal.  Once I started adjusting settings, I realized that the settings were off in a major way.  I had to get out of analog mode and into digital mode.  Once I did that, I was able to successfully capture my voice on Sound Recorder.  Thanks!  Problem solved :)

---

### Post by d3ngar on 2009-05-19
mikewu: This has certainly done the trick for me. Who would have guessed that capture is off?

Also strange that the capture settings are hidden in Volume Control. Seems that ubuntu wanted to make it difficult. Or maybe it's because they wanted to prevent audio-feedback?

I donno, my Skype is sorted now

---

### Post by ntrapped on 2009-06-25
Hi everyone,

I am new to Ubuntu - and am using Jaunty. 

I installed skype too...but the audio is still a problem.
kmix is installed and is latest,
capture is fine too...

what else can I do? 

Skype detects saying - problem with audio playback...

pls suggest

---

### Post by peterbiker on 2009-06-26
I'm a linux newbie with a Dell 1545.  I haven't been able to do anything (skype, sound recorder, etc.) with my mike.  If I try to record, it apparently runs at a crazy fast rate - it will say that I've recorded an hour of audio in about 10-15 sec.  

I reset the levels thru terminal according to the instructions above.  I'm not sure about the analog/digital thing.

In the volume control, there's a confusing array of choices under "Device".  Default is "HDA Intel (Alsa mixer)".  Does this sound correct?

Thanks!

Peter

---

