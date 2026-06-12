---
title: "Links in Evolution Mail Not Working, No Sound In Totem after upgrade (7.10 to 8.04)"
date: 2009-02-07
forum: Installation &amp; Upgrades
---

### Post by StewartM on 2009-02-07
Hello all,

Last weekend I upgraded some friends' Dell 530N computer, purchased with 7.10, to 8.04. (This was the 2nd such upgrade I assisted with in my role of local novice Ubuntu encourager-troubleshooter). The upgrade went fine (apparently) and the only problem encountered was the one listed on Dell's wiki site:

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/Desktop_Wont_Boot)

However, this week they are calling me to report 2 problems:

One, is that URL links in Evolution Mail no longer open;

Two, that movie files (.wmv formats) sent to them as Evolution attachments open in Totem and play but there is no sound.

I'll have to go over to troubleshoot the problem. .wmv attachments saved to disk play without sound the same as they do when opened by Totem in Evolution.

The first error may be as simple as going to System|Preferences|Preferred Applications and setting Firefox to be the default web browser. I'll also check the settings in Firefox itself.

The 2nd? When I did the upgrade, I changed the sound preference settings from "Autodetect" to "ALSA"; my friend confirmed that was still checked. (Some had already suggested this fix when I did web searches). Test sounds play fine. I checked music files when I was there, so I suspect they will still play fine. It's only in Totem where the problem occurs. They have only .wmv formats so I don't know (yet) if other movie formats likewise play without sound.

Any ideas on what this could be, and how I might help troubleshoot it and get it fixed? 

StewartM

---

### Post by StewartM on 2009-02-08
> **StewartM said:**
> 
One, is that URL links in Evolution Mail no longer open;

Two, that movie files (.wmv formats) sent to them as Evolution attachments open in Totem and play but there is no sound.

I'll have to go over to troubleshoot the problem. .wmv attachments saved to disk play without sound the same as they do when opened by Totem in Evolution.

The first error may be as simple as going to System|Preferences|Preferred Applications and setting Firefox to be the default web browser. I'll also check the settings in Firefox itself.

The 2nd? When I did the upgrade, I changed the sound preference settings from "Autodetect" to "ALSA"; my friend confirmed that was still checked. (Some had already suggested this fix when I did web searches). Test sounds play fine. I checked music files when I was there, so I suspect they will still play fine. It's only in Totem where the problem occurs. They have only .wmv formats so I don't know (yet) if other movie formats likewise play without sound.

StewartM

Update:

One, indeed setting the System|Preferences|Preferred Applications fixed the problem with Firefox not opening URLs in Evolution;

Two is more complicated.

a) Re-installing totem and totem-xine and related programs allowed video content (wmv files) to play once saved to disk with sound. It did not allow for them to be played in Evolution directly (as in "open with Movie Player);

b) Setting System|Preferences|Preferred Applications to use "Totem" for Multimedia playback as the default did not fix the problem (as per above with Firefox);

c) Setting the sound detection for music and movies from ALSA to "autodetect" *did* yield sound in wmv format when played directly from Evolution. This is surprising, as most have recommended setting the sound to ALSA to get playback in 8.04 (due to the PulseAudio bug).

d) However, DVD will not play properly (or will only play the introduction). LinDVD (this is a Dell) likewise will not play DVDs. So this seems to be a problem with the restricted formats.

Any ideas?

StewartM

---

### Post by StewartM on 2009-02-08
> **StewartM said:**
> Update:

d) However, DVD will not play properly (or will only play the introduction). LinDVD (this is a Dell) likewise will not play DVDs. So this seems to be a problem with the restricted formats.

StewartM

Following this tutorial: 

[http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/](http://ubuntu-tutorials.com/2008/07/01/enable-commercial-dvd-playback-on-ubuntu-804/)

Allows DVDs to play properly in 8.04 using Totem (like it did in Gutsy). LinDVD however still does not work at all.

I would have thought (since the Gstreamer plugins were listed as all enabled in the add/remove programs menu) that they would have updated likewise to play DVDs during the upgrade, but apparently they did not.

I'll mark this thread as "solved" though I will note that LinDVD does not work. I've tested other multimedia formats and they play as they should.

StewartM

---

### Post by StewartM on 2009-02-08
> **StewartM said:**
> 

I'll mark this thread as "solved" though I will note that LinDVD does not work. 

StewartM

Hmmm. Wonder why I can't mark this thread as "solved"? There's no "mark thread as solved" option under thread tools. (I posted parts of it from different computers with different internet IPs, I wonder if that's the problem?)

StewartM

---

### Post by dazzlindonna on 2009-02-08
The option to mark threads as solved has been removed as has the option to thank people.  Apparently, those options were a drain on forum resources.  I read this somewhere here on the forum in the last few days, but I'm afraid I don't remember where, so I can't link to the announcement.  I believe it said they would look into bringing that functionality back if possible, since they know how popular they are.  So, it's not just you - no one has the option anymore.

---

