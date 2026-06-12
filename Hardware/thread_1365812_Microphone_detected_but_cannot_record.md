---
title: "Microphone detected but cannot record"
date: 2009-12-27
forum: Hardware
---

### Post by llawwehttam on 2009-12-27
I have just bought a 
X65
                                             NNB-812
from novatech.

Everything works except for the graphics drivers but that is a known bug.
The webcam works but the mic input does not.

Any ideas would be appreciated.

---

### Post by bonfido on 2009-12-27
Well, you might have already tried it and this might sound odd to you:


Go to System/Preferences/Sound      

choose input tab,It might be disabled, just enable it and test it with your sound recorder.

---

### Post by coskierken on 2009-12-28
And, install "pavucontrol" through synaptics.  I had to do this on a new Acer D250 to get the built in mic to work.

---

### Post by sarthorks on 2009-12-28
type "alsamixer" in terminal, and make mic settings full/ unmute them if they are muted. there are sometimes two fields: front mic and mic, and their repsective boosts: make them full, and play around with different input devices in sound pref in system>preferences.

---

### Post by llawwehttam on 2009-12-28
Hmm, I tried everything above and there were two instances of front mic in alsa mixer ( i guess one is the boost), they were muted so I enabled them and i put them both to max but still no luck. Changing input devices in sound preferences makes no difference and in sound preference under input it does not appear to be picking anything up. Any more ideas??

---

### Post by llawwehttam on 2009-12-28
Just tried installing gnome-alsamixer front and front mic are at max as are both captures. The record button is ticked as well. Still no difference.

---

### Post by llawwehttam on 2010-01-04
still not fixed I'm afraid.
```
sudo bump
```

---

### Post by aljoriz on 2010-01-04
Try using a headset with Mic and connect it to the headset and mic jack.  See if it works, I have similar prob on 9.10 only to find out that for some weird reason the internal mic doesn't work but when using a mic via mic jack. It would work!

It's a good try as you won't be breaking anything.

---

### Post by llawwehttam on 2010-01-23
> **aljoriz said:**
> Try using a headset with Mic and connect it to the headset and mic jack.  See if it works, I have similar prob on 9.10 only to find out that for some weird reason the internal mic doesn't work but when using a mic via mic jack. It would work!

It's a good try as you won't be breaking anything.

External works but I really want the internal ones working.

```
sudo bump
```

---

