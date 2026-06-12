---
title: "Sound Problems"
date: 2008-07-27
forum: General Help
---

### Post by xxlbonafidelxx on 2008-07-27
I seem to be having audio problems with a few programs, like Skype and Firefox, they don't seem to have any sound. I am new to Linux, about two days, so I am not familiar with the sound settings yet. Firefox had audio earlier today. I do however get sound out of Rhythmbox and other programs(not sure how many though). Is there a problem with my current sound settings? I was messing with them earlier and don't remember the settings they were before. Any help would be appreciated.
Thanks!

---

### Post by sdennie on 2008-07-27
I would recommend going to System->Preferences->Sound and changing all the options to ALSA.  You will need to shutdown all applications that may use the sound card before you notice the change but, it should work.

Alternatively, you can try this guide to fix the existing sound system: [ HOWTO: PulseAudio Fixes & System-Wide Equalizer Support (Hardy Heron)]("http://ubuntuforums.org/showthread.php?t=789578")

---

### Post by xxlbonafidelxx on 2008-07-27
Thank you! I have got firefox working and skype working with a few changes, but when I use skype it says: "Problem with audio capture." Any ideas? I used the "test" with all of the options under sound capture but no luck(Test Sound worked).

---

### Post by sdennie on 2008-07-27
Try double clicking on the speaker icon in the top right corner of the screen and then going to Edit->Preferences.  Enable everything.  For me, in that application, I then have to go to the Options tab and then change the input source to digital.  Even if that's not the case, you may find something in that application that will fix your problem.

---

### Post by xxlbonafidelxx on 2008-07-27
Seems to be all working. Thanks a bunch!

---

