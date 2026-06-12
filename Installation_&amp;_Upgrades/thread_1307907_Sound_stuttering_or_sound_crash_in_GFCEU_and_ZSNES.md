---
title: "Sound stuttering or sound crash in GFCEU and ZSNES"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by paechan on 2009-10-31
I have an old computer in my living room that I have hooked up with a controller pad and the TV, meaning that it is basically a perfect emulator pc.

SO in Ubuntu 9.04 I have been using both GFCEU and ZSNES with no trouble at all. Sound has been fine and considering its an old Athlon xp 2100+, both of them ran really well.

After upgrading to 9.10, the sound is now completely screwed in these two applications. The sound seems to work fine for other purposes, such as music and movies, but these two emulators have some serious problems.  GFCEU crashes immediately with sound enabled and ZSNES has some serious stuttering issues combined with a very choppy rendering.

I have done the 9.04 -> 9.10 upgrade/fresh install on two very different computers and no matter what you do, the sound simply does not work.

I would really like to get this working again as both my girldfriend and I had really started to like playing mario together :D

I am writing this on another PC, but tell me if I need to run any commands to get info or something. I am more than willing to work on this.

---

### Post by paechan on 2009-10-31
Of the three computers I have done the upgrade, these two emulators don't work on any of them. I find it very unlikely that I am the only one with this problem.

---

### Post by paechan on 2009-11-02
Am I really the only one using emulators on my PC ?

---

### Post by zugol on 2009-11-02
Hi !

Got the same problem.
Last time (jaunty) libsdl1.2debian-oss and 44100HZ samplerate fixed it, but this trick not longer work with karmic.

[edit]

Try this trick and add "-ad oss" to your launcher

Works with terrific sound for me.

Actually I'm trying to get multiple emulators on my HTPC. 
Exchanging trick and workaround would be great.

---

### Post by thedogisdead on 2009-11-18
I'm having the exact same problems... anyone have any luck?  It's such a shame  :-(

---

### Post by strigare on 2009-12-25
> **thedogisdead said:**
> I'm having the exact same problems... anyone have any luck?  It's such a shame  :-(

What I did was install 

libsdl1.2debian-pulseaudio

and then start zsnes with the "-ad pulse" option, and now it sounds perfect :)

---

### Post by Andysan on 2010-01-04
> **zugol said:**
> Hi !

Got the same problem.
Last time (jaunty) libsdl1.2debian-oss and 44100HZ samplerate fixed it, but this trick not longer work with karmic.

[edit]

Try this trick and add "-ad oss" to your launcher

Works with terrific sound for me.

Actually I'm trying to get multiple emulators on my HTPC. 
Exchanging trick and workaround would be great.

"-ad oss" worked great for me, cheers.  Reminiscing when Starfox used to entertain me for hours!

---

### Post by sergioadh on 2010-01-23
nice job with the "ibsdl1.2debian-pulseaudio", it did the work for me .. also running "zsnes -ad pulse" tyvm

---

### Post by rdvon on 2010-04-02
> **zugol said:**
> Hi !

Got the same problem.
Last time (jaunty) libsdl1.2debian-oss and 44100HZ samplerate fixed it, but this trick not longer work with karmic.

[edit]

Try this trick and add "-ad oss" to your launcher

Works with terrific sound for me.

Actually I'm trying to get multiple emulators on my HTPC. 
Exchanging trick and workaround would be great.

This works amazingly well! You're the best! I seriously can't thank you enough! :D

---

### Post by zugol on 2010-04-05
Helping someone is a reward for me ! :)

I think Lucid will come with a lot of work and tweaking... Or it will works out of the box ?

---

