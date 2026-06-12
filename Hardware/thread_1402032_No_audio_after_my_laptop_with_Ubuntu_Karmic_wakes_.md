---
title: "No audio after my laptop with Ubuntu Karmic wakes up"
date: 2010-02-08
forum: Hardware
---

### Post by inameiname on 2010-02-08
[B]When I close  the lid of my notebook computer and it goes to sleep and then awake,  there is no audio. I have read a few other's postings and have found  that this has happens on more than just mine. I've installed the very  same Karmic custom DVD onto other computers, including laptops, and  sounds works after wakeup on them just fine. So I suspect there is  something with my Gateway that is causing it. In the end, I have to  reboot simply to get the audio to return.

So if there is anybody that has found a solution to this problem that  would be great. I've heard a similar issue occurred with the Hardy  version of Ubuntu as well but I haven't found it's solution either. [/B]

---

### Post by IcarusR on 2010-02-08
From a terminal try 

```
sudo killall pulseaudio
```

Then

```
pulseaudio & exit
```

---

### Post by inameiname on 2010-02-09
Thanks for the suggestion, but I'm afraid I tried that very thing before and it didn't help. It seems the issue is that something is not telling the audio to awake from it's slumber once the lid opens.

---

### Post by inameiname on 2010-03-03
On a suggestion from this board, I decided to try seeing if the problem remains with Lucid. 

Unfortunately, trying Ubuntu Lucid's Alpha version (upgrading Karmic to  Lucid), just to see if it's possible a solution would be  found, the  very same audio problem occurred, no sound on opening/resume after  closing the lid and waiting for several minutes while the computer was  asleep. 

The very same audio files were played/used, from right before my  experiment and right after, and again, no sound once I woke my laptop  up.

Guess then whatever update that was done with the audio or it's  dependents which causes this problem from Jaunty to Karmic seems carried  over to Lucid as well; at least the Alpha version. 

So as it stands, the issue did not occur in Jaunty (that was my first  experience with Ubuntu and thus, do not know about past versions), but  does happen in Karmic, as well as in Lucid's Alpha release so far. Thus,  I still don't have a solution. :(

The only thing I can think of that might be at fault here with my  experiment is that I didn't install a fresh Ubuntu Lucid Alpha install,  but an upgrade from Karmic. It may very well be something left from  Karmic.

---

### Post by inameiname on 2010-03-03
Okay, so a quick update.....I decided to try a fresh install of Ubuntu  Lucid Alpha 3 to see if it may have fixed the issue, and sadly it did  not.

Doing the very same thing, no sound was achieved after opening up the  lid. In addition, a 'program has crashed' error popped up regarding  something called "indicator-sound-service'.

Oh, and I forgot to mention, most times, when the sound does not 'wake  up', also messed up by this problem is video, as it seems more jumpy,  slow, and not quite right. Not always, but often. Now, EVERYTHING is  fixed just fine and dandy once I restart the computer.

---

### Post by inameiname on 2010-07-09
I just wanted to say that some update just in the past few days has  fixed this issue that I've been having this Karmic.

Hopefully it's not a fluke. Seems to be working. I'll mark this as  solved anyway.

I'm curious though as to which update it was, and whether it's a fix  everybody else who has had this issue too has found as well. 

Feel free to comment on it if you have, or have not.

I also wonder if it's an official update that fixed it, or an update  from one of my PPAs. It would be great to know so as to figure out what  could change it again if and/or when it happens again in another Ubuntu  release. 

Finally!!!!!!!!!!!!

---

