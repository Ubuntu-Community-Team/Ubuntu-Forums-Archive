---
title: "&quot;no soundcards found&quot; after tweaking alsa"
date: 2010-06-01
forum: Hardware
---

### Post by mileniasm on 2010-06-01
I totally messed up my audio today, after an attempt to fix my mic in Skype... which seems to be a common problem with Ubuntu...

I did what I did (I don't even remember all of it now) and now I don't have ANY sound - not just the mic - the speakers, the headphones, system sounds... nada...

When I type in the console "aplay -l" it says:
$ aplay: device_list:223: no soundcards found.

Alsamixer is totally gone from the system:
$ alsamixer
$ cannot open mixer: No such file or directory

I don't know what to do anymore. I've spent probably half the day trying to fix this problem and none of the threads in this forum works. 

I have an Asus eee pc 1001HA. It uses an HDA Intel card but I don't remember the driver model, otherwise I would have downloaded it already. :(

Please help!!! I love my little netbook and Ubuntu. I have a Sattelite and I'm planning on getting rid of Windows there too, but since I'm pretty new at terminal-ing, I'm hoping to fix my problems on the Asus first, and then go all Ubuntu. Open source rocks!!!

:guitar:

---

### Post by Yellow Pasque on 2010-06-01
It would help if you could tell us what you've done to "fix" your netbook. :P
My guess is that you need to remove any alsa-backports packages you installed and follow this: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

---

### Post by mileniasm on 2010-06-03
Gosh, I don't remember all the things I did - updated alsa backports, removed pulsaudio and then I put it back... I think I also removed alsa and then tried to install it again, but this time through the Synaptic Package Manager (everything else I did through the terminal). Oh, I also added a new line in the alsa main file - the *options* snd-hda-intel model=auto - but since that did not work (and I tried typing in different models), I removed the line and saved the file as it was before I tried to change it...

I spent minimum 1 hr on this, going through the forums and trying different things, so I'm sure I've done a lot of damage... I wonder if the best option is to just re-install... I got Lucid Lynx through the update option, so maybe if I just do a fresh install things would work better?

---

### Post by Yellow Pasque on 2010-06-03
That doesn't sound too bad. Remove the alsa backports package and try the script I linked to above.

> I wonder if the best option is to just re-install
If you have your /home directory on a different partition than / (root), it may be easier. If you don't, it's a pain to back up your personal data and re-customize everything.

---

### Post by mileniasm on 2010-06-03
Thanks for your help Temüjin. Right now I'm pressed for time (master thesis and all that jazz), but I think I'll re-install later this month. I appreciate you trying to help me though :)__

---

