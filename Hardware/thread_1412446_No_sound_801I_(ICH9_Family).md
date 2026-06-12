---
title: "No sound 801I (ICH9 Family)"
date: 2010-02-21
forum: Hardware
---

### Post by erjoalgo on 2010-02-21
I have not had sound since I installed Ubuntu. I installed Ubuntu 9.10 directly.
I've searched around several forums and tried different things with no luck.
My system is 64bit, Dell Studio latptop. 

This is my audio device:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

I will provide any information upon request. I am certain I am not alone in this problem.
Thank you

Also I should add that, unlike other users who hear sound at start up, I do not.

---

### Post by IcarusR on 2010-02-21
There are several different solutions in this thread...

[http://ubuntuforums.org/showthread.php?t=1316634]("http://ubuntuforums.org/showthread.php?t=1316634")

Post 6 here talks about adding user to audio group... also other stuff if you have intel audio card.

[http://ubuntuforums.org/showthread.php?t=1384181]("http://ubuntuforums.org/showthread.php?t=1384181")

---

### Post by erjoalgo on 2010-02-21
Thanks but I already tried that solution. In fact, it is not even my problem as my Ubuntu does recognize my sound card. I don't even hear any sound at startup. When I boot into Windows, however, everything is fine.

---

### Post by erjoalgo on 2010-02-23
Update: I randomly got this error after hibernating my system:

 p, li { white-space: pre-wrap; }  KDE detected that one or more internal sound devices were removed.
 Do you want KDE to permanently forget about these devices?
 This is the list of devices KDE thinks can be removed:
 
[LIST]
[*]Capture: HDA Intel (STAC92xx Analog)
[*]Output: HDA Intel (STAC92xx Analog)
[/LIST]


Any ideas?

---

### Post by erjoalgo on 2010-02-25
*bump*
I tested the mic on my system, and it works (the sound level indicator bar moves with one's speech).
The sound card output is recoginzed according to System>Preferences>Sound.
Is this sound card even supported by Ubuntu?
801I (ICH9 Family)

---

### Post by erjoalgo on 2010-09-30
This is solved in the last ubuntu release.
No sound through headphones problem can be fixed by adding option to a file. Google position fix, options, snd hda.

---

