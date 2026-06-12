---
title: "USB headphones work with Youtube, but not with other websites..?"
date: 2017-09-29
forum: Hardware
---

### Post by mccarthyemmet on 2017-09-29
Hi everyone,
 my USB headphones are working fine for YouTube, but for other sites I where I need sound e.g. Udemy or Rosetta Stone the sound comes out over the speakers. It seems the headphones don't recognise the headphones when the website launches a new window. The Left / Right test under Sound works fine. Headphones plugged into the normal audio jack work fine. I'm running Ubuntu 16.04 LTS , and Firefox. Any help much appreciated, as I am a total Linux beginner... Emmet

---

### Post by kostkon on 2017-09-29
I'm guessing those sites are using a Flash-based player for their media.

You could try the following: install PulseAudio Volume Control (pavucontrol), launch it, then visit one of those sites and start a video or audio clip, then in the Playback tab of your pavucontrol window you should see Flash being listed there. Just change the device for it from your internal audio to your USB headphones. PulseAudio will hopefully remember your choice from now on.

Hope that helps.

---

### Post by mccarthyemmet on 2017-10-01
Didn't work I'm afraid. The pavucontrol doesn't see the windows. Thanks any way...

---

