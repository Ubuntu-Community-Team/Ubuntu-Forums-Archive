---
title: "I want to get the rest of my sound system to work"
date: 2008-12-05
forum: Hardware
---

### Post by mpc350 on 2008-12-05
Hi everybody, 

I have a new Lenovo Ideapad Y530 and it comes with 4 speakers plus a subwoofer (yeah, it's a little crazy on a laptop).  Well, I wanted to see if I can make them all work they way they're supposed to.  Currently just the two main L+R speakers are working, and I don't see how ALSA can support a multispeaker setup.  Can JACK help me with this?  Is there an expanded version of ALSA?  Any help would be awesome, 
THanks
Matt

---

### Post by Coburn Roar on 2008-12-08
I got the sound to work most of the way; however, I still haven't figured out how to mute the sub-woofer when headphones are plugged in. This post is about Y510s but most of the volume stuff works.
[http://ubuntuforums.org/showthread.php?p=4427198](http://ubuntuforums.org/showthread.php?p=4427198)
Make sure to get the newest version of alsa though. Originally, I used the version they used and it didn't work. Also, on the volume control menu add center, surround, and LFE. Also, change the channels form 2 to 6 in options and enable IEC958.

If you can figure out the muting issue with the sub-woofer, help would be appreciated.  (I followed the instructions on the link, but only the 2 front speakers mute with headphones.)

---

