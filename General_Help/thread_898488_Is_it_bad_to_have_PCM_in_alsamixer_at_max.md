---
title: "Is it bad to have PCM in alsamixer at max?"
date: 2008-08-23
forum: General Help
---

### Post by Arrowx7 on 2008-08-23
Hello,
Everything was very quiet out of the speaker (I have a Thinkpad T61).
I looked at the alsamixer, and boosted my PCM up to 100%. My master is usually at 60%-90%.

Now I'm worried if having PCM at 100% going to damage my hardware?  Will something overheat or something?  

Thanks!

---

### Post by sdennie on 2008-08-23
It shouldn't be a problem.  You'd notice the sound being distorted by the loudness well before doing damage to the speakers I think.

---

### Post by caljohnsmith on 2008-08-23
Just as a point of interest, setting PCM volume to > 74% means that Alsa digitally amplifies the audio signal, which can lead to distortion as vor mentioned. How "loud" your original digital audio signal is will determine whether you get distortion or not by setting PCM > 74%. In general it is best to use PCM set to 74% and then adjust master volume for overall volume level. If you still can't get enough volume setting master vol to max, then you could run up PCM volume higher. 

The overall volume level coming out of your speakers is what will determine whether your speakers could be damaged, not how each individual volume level is set in Alsa. Usually it's easy to hear the distortion resulting from the speakers being driven too hard, so that would be the time to back down on the overall volume. :)

---

### Post by sdennie on 2008-08-23
> **caljohnsmith said:**
> Just as a point of interest, setting PCM volume to > 74% means that Alsa digitally amplifies the audio signal, which can lead to distortion as vor mentioned. How "loud" your original digital audio signal is will determine whether you get distortion or not by setting PCM > 74%. In general it is best to use PCM set to 74% and then adjust master volume for overall volume level. If you still can't get enough volume setting master vol to max, then you could run up PCM volume higher. 

The overall volume level coming out of your speakers is what will determine whether your speakers could be damaged, not how each individual volume level is set in Alsa. Usually it's easy to hear the distortion resulting from the speakers being driven too hard, so that would be the time to back down on the overall volume. :)

That's very useful information.  Thanks.

---

### Post by Arrowx7 on 2008-08-25
thanks guys

---

