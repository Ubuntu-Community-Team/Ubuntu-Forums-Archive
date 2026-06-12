---
title: "Sound problem on Thinkpad R61"
date: 2008-11-19
forum: Hardware
---

### Post by busfahrer on 2008-11-19
Hi,

I have a Thinkpad R61, which according to the internet has an AD1984 soundchip. I knew from reading several reviews that the speakers on this laptop are bad, so I was prepared.
However, even when I plug in headphones and listen to a normal song via headphones, the sound is really bad and kind of crackling. Really not something one could listen to for a long time. (The headphones work fine with the same song on another PC).

Could this be a configuration problem of any sort? Or is it just a very bad quality audio jack?

By the way, I'm using Ubuntu 8.10.

Greetings, busfahrer

---

### Post by CyberPrime on 2008-11-19
try playing with the sound options in the volume control (Right click on the volume control in the top right corner, Click Open Volume Control). If that doesn't do anything I would say it's bad hardware. Apologies.

---

### Post by WarWizard89 on 2008-11-28
I had the exact same problem with my R61. I found that lowering the PCM volume in the volume control menu made that crackling go away. Then make sure you set the volume to control main the main slider instead of PCM. Hope that helps.

---

### Post by zshuford on 2008-12-15
War Wizard is exactly right.  Lower your PCM volume to fix this issue.  You can do that with Gnome ALSA Mixer in the repositories.

---

### Post by girark on 2008-12-31
I too am using 8.10 on an R61, and I'm having what sounds like the same problem. Any time my master volume exceeds about 30%, the quality goes south. The R61 speakers aren't the best, but they do the trick, and I'd like to be able raise the volume higher than I am now. I do not believe this is a hardware issue, as I was able to increase the volume to ~100% without a decrease in quality when I was using Vista.

I have the mixer set to HDA Intel (Alsa mixer), and have tried both 'Master' and 'PDM' without noticeable difference.

Any thoughts?

Thanks.

---

### Post by girark on 2008-12-31
I have solved my problem with the audio. If you're still having issues:

In your sound settings: set Default Mixer Tracks Device to HDA Intel (Alsa mixer) and select "Master". Pull up the sound menu - set the master volume to maximum, then play a song or movie. While that's playing, adjust the PCM volume to the highest level where you still get good quality and then close it. From now on, you'll control via the master volume (which will be controlled by your vol up and down buttons on your keyboard.

My quality is now up to the level that it was when I was running Vista.

---

### Post by piotrekno1 on 2009-11-16
Guys! for any problems concerning R61 Thinkpads look here: [https://launchpad.net/~c4pp4](https://launchpad.net/~c4pp4). Just added this PPA and upgraded and all the problems where gone, not only the one with the microphone.

---

