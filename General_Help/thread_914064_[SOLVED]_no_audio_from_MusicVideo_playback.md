---
title: "[SOLVED] no audio from Music/Video playback"
date: 2008-09-08
forum: General Help
---

### Post by Kymus on 2008-09-08
After upgrading to Hardy, I have had some major audio issues. Now to be clear, this is only when I try to play music or video in a player; all audio and video seems to work fine in my web browser (embedded video works fine as does internet radio), and before I upgraded to Hardy, I had no audio issues at all. :confused:

In *Amarok*, *VLC*, *Kaffeine*, and *Movie Player* I never get audio, regardless of what I try to play. However, there is one exception: MPlayer; when playing video in that, I get audio just like normal. I just tried playing audio in MPlayer as well and it seems to play them fine (though it does seem a little unstable when I tried straight audio files, but that could be a separate issue).

The sound card I'm using is the on-board one from my motherboard (**Foxconn NF4UK8AA**).

---

### Post by skullmunky on 2008-09-08
Not near my ubuntu machine at the moment - but in the player apps, have you looked through the preferences to see if there are sound hardware settings you can try changing?  For example, trying different ALSA, or OSS, or PulseAudio options.  

Try posting in the "Multimedia" forum too - I'm sure this is fixable.

---

### Post by Kymus on 2008-09-08
Thankfully, the solution was that simple. The old settings were on auto detect; changing to alsa did the trick.

thank you very much :)

---

