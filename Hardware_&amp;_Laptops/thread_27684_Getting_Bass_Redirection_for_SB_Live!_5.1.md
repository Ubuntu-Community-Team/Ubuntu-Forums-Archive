---
title: "Getting Bass Redirection for SB Live! 5.1"
date: 2005-04-17
forum: Hardware &amp; Laptops
---

### Post by Ciddan on 2005-04-17
I've just made The Switch over to Linux and Ubuntu and I'm having some sound issues. I've got a basic SB Live! 5.1 card and sound isn't exactly great.

**[Edit = Fixed with Wave Surround controls]**
First of all, I can't get the 5.1 sound to work at all. I've switched to ALSA and added some controls in the volumecontrol, but I can't figure out how to get it to work properly.
**[/Edit]**

Secondly, I get almost no bass output at all. In Windows there was an option for the soundcard to use Bass Redirection, meaning that the soundcard used the centre-channel to output all the bass. Is there a way to do this in Linux?

Thirdly, I get sound distorsions while playing on high volume, which is annoying as hell.

Since I'm new to Linux any help provided would be highly appreciated.

---

### Post by skoal on 2005-04-17
I have a soundblaster 5.1 and it sounds great.  

The best way to test/adjust is to start a song/mp3 in XMMS (or the like).  Open up a terminal and type 'alsamixer'.  Then, at least for 5.1 surround using your SB Live!, adjust these controls:

Wave
Wave Center
Wave LFE
Wave Surround

* use the up/down arrows for +/- and 'm' button to mute/unmute channels.  When you're done, hit ESC.  If you want to save those settings, then type 'alsactl store'.  You may have to mute some channels to get rid of a hiss or loud crackle.

---

### Post by Ciddan on 2005-04-17
[QUOTE=skoal]I have a soundblaster 5.1 and it sounds great.  

The best way to test/adjust is to start a song/mp3 in XMMS (or the like).  Open up a terminal and type 'alsamixer'.  Then, at least for 5.1 surround using your SB Live!, adjust these controls:

Wave
Wave Center
Wave LFE
Wave Surround

* use the up/down arrows for +/- and 'm' button to mute/unmute channels.  When you're done, hit ESC.  If you want to save those settings, then type 'alsactl store'.  You may have to mute some channels to get rid of a hiss or loud crackle.[/QUOTE]
 Well, now I've got some sound in my Sub :) Yay for that! However, bass is still really weak using headphones. I can't get that last depth that I want. I noticed disabling AC97 helped to remove almost all distorsion while I'm using headphones, which is great. I guess I'll have to turn to software EQ's for the final tweaks. Thanks for the assistance.

---

### Post by skoal on 2005-04-17
I've attached my 'asound.state' file if you want to compare between the two. That file is located in /etc.  If you want to try out mine, you might want to move/copy yours first as a backup.

---

