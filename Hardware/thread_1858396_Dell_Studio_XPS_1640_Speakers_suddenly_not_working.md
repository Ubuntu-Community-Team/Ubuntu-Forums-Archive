---
title: "Dell Studio XPS 1640: Speakers suddenly not workings :S"
date: 2011-10-12
forum: Hardware
---

### Post by astrobob.tk on 2011-10-12
Hello,

Yesternight,  everything was working. Suddenly I lost my downloads in the Downloads directory (see: [http://ubuntuforums.org/showthread.php?t=1858193](http://ubuntuforums.org/showthread.php?t=1858193)).

Moreover, I just realized today, that the speakers are not working :S
I tried the jack with a headphone & it works, but not the speakers!

I checked the volume control & made sure the devices are correct, but still not working.
I tired searching for a solution but most do not give a definite answer.

One solution is about alsa backports; another is adding a line to 

the things is that i didn't face such a problem before. Its quite weird to be working & suddenly stop.

I'd like to mention that 2 days earlier, I opened the back of the laptop  & cleaned the fan from dust. I read that there is a hardware that disables the speakers if a headphone is connected. But the point is that after I did that, the speakers were working.

threads i checked:

[http://ubuntuforums.org/showthread.php?t=1808599](http://ubuntuforums.org/showthread.php?t=1808599) :: couldn't install the backport b/c I couldn't find the package + i am reluctant about adding those line(s) before asking someone.

I tried adding ```
options snd-hda-intel model=dell-m6 enable_msi=1
```to /etc/modprobe.d/alsa.conf

(which btw was empty! i guess it should have been alsa-base.conf instead) but nothing happened. I also replaced that line withI should also note that I booted into the installed Win7 & the problem persists.


Could you please help ?!! It would be better if we go through this from the beginning in case I missed something.

thanks

---

### Post by astrobob.tk on 2011-10-12
Update:

Just a few minutes ago, I was listening to music through the surround speakers which I plug in the headphone jack. Interestingly, I wanted to close the music; I removed the jack port before I stopped the music, &&&& the speakers worked!!!

I plugged it back in & then out & the speakers did NOT work. Repeated this several times & I had another hit; the speakers worked. Now they are working; am reluctant about plugging in anything in those jacks.

The laptop is 1 year old (with me; i bought it new). What do you think is the  problem ?!

---

