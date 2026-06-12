---
title: "Skype Mic noisy w/ Ubuntu Remix on Lenovo S10-2"
date: 2009-08-29
forum: Hardware
---

### Post by grimace on 2009-08-29
After hours of research and numerous failed attempts, I finally got my Lenovo S10-2's mic to function on Netbook Remix.... sort of.  Feedback is an issue because the mic must be boosted to pick up my voice.  Also, because the gain must be set high there is an unacceptable amount of hiss.  I've tried playing with the mixer, but cannot get the hiss to an acceptable level.  Does anyone have suggested settings for Alsa mixer/Skype in order to make the mic function with decent clarity?

---

### Post by deanerk on 2009-09-04
I also have the Lenovo S10-2 with UNR.  I know I read something about fixing audio here and I have to find that again as I need to have mine turned nearly all the way up to get sound.  If/when I find it I'll post back.  I am using a Logitech wireless laser mouse and on a couple occasions have heard some loud and really annoying feedback.  Never seems to happen when I'm not using the mouse, yet doesn't always happen when I am using the mouse...  

I installed Skype and have not yet invested more than an hour or so in getting my webcam and internal mic to work.  Both do not work currently.  Can you fill me in on fixes or point me to some threads you may have used?  So far my searches have sent me on tangents and I haven't found a lot specifically addressing my issues on the S10-2.  I have some time this weekend and would like to get this nifty little guy fully functional.  Thanks!

---

### Post by deanerk on 2009-09-04
Okay, updated ALSA to 1.0.20 and the mic works, but I see what you mean about having to crank up the mic and the feedback and all.  For anyone interested, I used this to upgrade ALSA --> [http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)  Worked great for me.  

So, has anyone else out there seen this audio issue?  I'll keep digging around.  Now that I do have some audio though, I'll probably shift my focus to getting my webcam to work.

---

### Post by deanerk on 2009-09-04
Duh...  Fn + Esc to turn on camera.  Guess I'm at the same stage as you are now grimace - working, but not optimally.

---

### Post by grimace on 2009-09-10
oddly enough, Skype works fine with my lenovo S10-2's internal mic ONLY on the initial call that I make after launching Skype IF it is to a land line phone or the Skype Test Call.  Attempting to call another Skype user always results in the receiver hearing loud static.  Any subsequent calls after the initial successful call also fail....hmmmmm....

---

### Post by pngwen on 2009-09-21
I had trouble getting my internal microphone working with skype.  The first thing I tried was upgrading my ALSA drivers, and that did get it working somewhat, but I was having the same problem that grimace was having.

So after a bit of tinkering, I discovered a way to work around that little problem.  If you go into skype's options->Audio Devices and then uncheck the box next to "allow skype to automatically adjust my mixer levels" it will fix the one call only bug.  Sure you lose automatic gain adjustment, but it does make skype work.  

After doing those two things, my Skype experience is beautiful.  I have been sending and receiving calls all day without issue!

---

