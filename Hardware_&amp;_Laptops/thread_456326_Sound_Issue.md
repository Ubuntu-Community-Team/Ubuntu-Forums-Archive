---
title: "Sound Issue"
date: 2007-05-27
forum: Hardware &amp; Laptops
---

### Post by simonrose on 2007-05-27
Hi all,

I am very new to Ubuntu and am a little unsure of myself. I have managed to get by with most stuff and pick stuff up along the way and get loads of stuff installed.
My problem is that I can listen to music and hear sound no problem (using Songbird) but if I try and play music through anything else (mplayer, or whatever automatically loads to run it) I dont get sound. the same is with video, I see the images but no sounds.

Even the login sounds do not work. however when I run the test sounds i get the continuous beep and can hear it. my sound card is a Creative Labs Sound Blaster 5.1 Digital card.

This has happened, I think, since I installed songbird. Is it just because songbird is a beta and this is a bug?

A friend of mine suggested that it may be that songbird is taking the audio driver and not releasing it for other applications? If that is it how do I get round it?

Cheers for any help!

Simon

---

### Post by spin2cool on 2007-05-27
After a fresh reboot, try running one of the programs you're having problems with (mplayer, etc) to see if you hvae sound.   If you do have sound in that situation, but not after you run Songbird, it's likely that your friend's hunch is correct.

If songbird is locking up the audio, you may be able to kill it manually.  If you're using the esd driver, for example, you'd use the command 'killall esd'. 

I'd probably also suggest trying some of the other audio jukebox programs available (amarok, banshee, rhythmbox, etc).  Songbird is a great concept, but in my experience the bugs aren't worth the hassle right now.

---

### Post by simonrose on 2007-05-27
I did a reboot and still couldn't get sound through mplayer.

How do I tell if I am using esd driver or what driver I am using and how I go about killing it!

---

### Post by simonrose on 2007-05-28
that is really odd. i uninstalled songbird and then put banshee on instead. still had the same issue.

rebooted and then it worked. got sound and all was good in the world for about 5mins. then there were some updates to be installed...installed them and now i have no sound on my video again.

music still plays.

---

### Post by simonrose on 2007-06-02
any other thoughts?

---

### Post by crimsun on 2007-06-03
> **simonrose said:**
> any other thoughts?

This is symptomatic of one application hogging the sound device (on audio hardware that doesn't support PCM muxing).  You can list the applications using the sound device by using the following command in a Terminal/Konsole: `sudo lsof /dev/dsp* /dev/snd/* /dev/audio* /dev/mixer*`.

---

