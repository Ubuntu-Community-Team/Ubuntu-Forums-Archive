---
title: "Timeline 5810T Hardware help"
date: 2010-03-04
forum: Hardware
---

### Post by CJay554 on 2010-03-04
Hey guys, i have a few problems with the Timeline 5810T laptop. I have three things that don't work:

-Brightness change
-Microphone
-Mouse Pad "Lock" button

Fix for brightness is [http://ubuntuforums.org/showthread.php?t=1223701&highlight=5810t&page=3#25](http://ubuntuforums.org/showthread.php?t=1223701&highlight=5810t&page=3#25)

Microphone doesn't work at all with any of the "driver" selections

Mouse pad "Lock" button turns mouse off (for when typing on a computer the touchpad doesn't get moved) but when i press it again it will not turn the mouse back on. I have to restart. Any ideas?


[SOLVED]  (for mic)
1. Install pavucontrol from synaptic or apt-get
2. Go into Applications > Sound and Video > PulseAudio Volume Control
3. Go to "input" tab
4. Click on the "shield" icon or lock icon to unlock the channels
5. Slide the "Front Left" slide to 10%

---

### Post by CJay554 on 2010-03-07
Bump =( has anyone found a fix for the mic at least?

I might have found a potential fix: [http://www.linlap.com/wiki/acer+aspire+timeline+5810t](http://www.linlap.com/wiki/acer+aspire+timeline+5810t)
using model=acer for the snd_hda_intel module... anyone try this? Will report when i attempt to fix.

---

### Post by CJay554 on 2010-03-17
that link doesn't really explain much, the snd_intel is only for the sound itself, nothing about the microphone.

Though i did read that i can fix the microphone by installing the alsa backports via synaptic, which worked fine!

My microphone can be read just dandy! though skype doesn't read it... which is weird...

neither does alsamixer? but it works fine in the sound recorder program...

Alsa mixer registers as HDA Intel G45 DevCTG device. The Capture view has 2 entries, front mic, and capture. Capture is what controls my microphone, though i have no idea what the front mic entry is or does...

Also in the right click in the sounds icon on the system tray, and in sound preferences my input isn't registered. Its using the internal audio analog stereo. But the input level never changes... very very odd...

Skype registers my microphone with pulseaudio, even though nothing really shows...

so yeah, a few bugs everywhere! im confused at what to do next.

Help please =(

---

### Post by rbrown3rd on 2010-05-10
Sorry, no help but just to know I am having the same problem.  Cheese works with the vidcam and sound recorder works with the microphone but neither works with Skype.

---

### Post by rbrown3rd on 2010-05-10
[This thread]("http://ubuntuforums.org/showthread.php?p=9275542#post9275542") might help with the sound.  Download Pulse Audio Volume Control.  Unlock the stereo sliders and slide one of them down to 90 percent or less.  Audio should work then.

---

### Post by CJay554 on 2010-07-22
YES!!! thank you so much ^.^
by the way its called "pavucontrol"
everyone has it as "pauv control" but thats the wrong app to search for in synaptic...

But thank you so much for the heads up!!! ^.^


[SOLVED]
1.  Install pavucontrol from synaptic or apt-get
2.  Go into Applications > Sound and Video > PulseAudio Volume Control
3.  Go to "input" tab
4.  Click on the "shield" icon or lock icon to unlock the channels
5.  Slide the "Front Left" slide to 10%

One question though... it seems to turn off quite often, turns lock on channels back on, and i have to do this constantly... any way to change this?

---

### Post by Carl.Spackler on 2010-09-18
> **CJay554 said:**
> 

Mouse pad "Lock" button turns mouse off (for when typing on a computer the touchpad doesn't get moved) but when i press it again it will not turn the mouse back on. I have to restart. Any ideas?



Did you ever find any solution for this part?

UPDATE: Found a solution. See this post

[http://ubuntuforums.org/showpost.php?p=9862780&postcount=43](http://ubuntuforums.org/showpost.php?p=9862780&postcount=43)

---

### Post by blogmaniak on 2010-12-11
Any luck with finding a permanent and graceful fix for the mic issues. I tried the pavucontrol thing but that does not really work. After setting the left to 10%, when I use google talk to make a call, it automatically resets back to locked and 53%. This kills the mic instantly.

---

### Post by eyeguyNOLA on 2011-01-18
<bump>

Also, another question:

How do I activate the numeric keyboard? It initially didn't work.
A few months later I noticed it was working. Then one day when I typing a report, I kept hitting the NumLock instead of Backspace
and the numeric keyboard no longer seems to want to work.

Rather, it seems to function as a "mouse" control inspite of me trying to toggle the NumLock key.

Any fixes on the brightness issue.

Also, how do I use the DVD player? I have yet to figure out how ot play DVD's on this machine since there is no hard button to open the DVD drive.

---

### Post by mathieu.racicot on 2011-01-31
Get all the things you need here.
[https://help.ubuntu.com/community/AspireTimeline](https://help.ubuntu.com/community/AspireTimeline)

---

