---
title: "Realtek ALC272 headphone problem"
date: 2009-10-12
forum: Hardware
---

### Post by LadFromWales85 on 2009-10-12
Hey all,

I recently bought a Packard Bell Dot MA 11.6" notebook, which has been fantastic in every regard.  I've used it with headphones a few times before, but have never noticed that when headphones are plugged in, audio randomly comes out of the speakers in sharp bursts.

The issue goes away if I lower 'Master' to -16dB, but at this point the headphones are very quiet.

The card is a 'HDA ATI SB' with chip 'Realtek ALC272'.

Alsamixer has controls for Master, Headphone, PCM, Front, Front Mic, Front Mic Boost, and Beep.
Muting Headphone mutes the headphones if they are plugged in, and no sound comes from the speakers.
Adjusting or muting Front also effects the headphones.

Am I right in thinking that as I can mute the headphone socket, the socket is auto sensing rather than mechanically switched?

Would it be possible to mute the speakers but not the headphone socket?

Pretty annoyed now that I've noticed this issue :(

Any help really appreciated :)

---

### Post by dabl on 2009-10-12
That particular sound chip is a bit of a problem at the moment -- it appears that a patch for the ALSA driver for 9.10 may be in progress, but that won't be released for a while yet.  For my Toshiba NB205, I have installed and configured OSS and it works well that way (well, I can't testify about the headphones, but the speakers work).  Here are some links for your reference:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/389040)

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1673617.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1673617.html)

[http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+dynabook](http://ubuntuforums.org/showthread.php?t=1215665&highlight=toshiba+dynabook)

---

### Post by LadFromWales85 on 2009-10-12
Cheers for the links, will have a read into it!

options snd-hda-intel model=asus-mode4 give me no luck, so I tried 1 and 2...2 give me a speaker slider and separate headphone slider and mute, but no sound through headphones at all.  Interestingly, the speakers do not mute at all when headphones are plugged in.  I just need to find a way to mute the speakers but not the headphone jack!

Trying mode3 now...

---

### Post by dabl on 2009-10-12
Depending on how you use it, it's fairly quick to install OSS and check it out that way, and if you don't like it you can go back to ALSA.

[https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

---

### Post by LadFromWales85 on 2009-10-12
Will have a look later, that all looks like it'll take more than a couple minutes, probably something I should do when I have a bit more time to spare :)

It's probably worth mentioning that I am using Arch at the moment, and the sharp blips of sound when headphones are plugged in also happen in Windows.

I'm thinking there must be a way to disable just the speaker output, either permenantly or switched.  The problem is bearable at the moment as I can just turn it down by 16dB to stop the glitches coming through the speakers when other people are around.

I will give OSS a go later on this evening :)

---

