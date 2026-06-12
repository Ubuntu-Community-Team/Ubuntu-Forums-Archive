---
title: "Audigy 2zs notebook wrong driver + Digital Output"
date: 2009-11-13
forum: Hardware
---

### Post by th3voic3 on 2009-11-13
Hi,

since I upgrade to Karmic my Audigy 2 zs notebook is displayed as a Audigy 2 Value.
While the command
```
aplay -l
```

still shows the notebook card.

Additionally I still can't get digital audio to work. In this [list]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs") it says that this function is not supported for the audigy 2 zs notebook, but the last entry is from 2006. So does anybody know anything about that?

---

### Post by Probable on 2009-11-30
I have the same problem except that mine doesn't even show up with ```
aplay -l
```

```
lspci
```shows my card as an Audigy2 Value. It is an Audigy 2 zs notebook. I wouldn't care, but it won't show up anywhere else, not in sound preferences, not in aplay. The sound card was working until I did a fresh install of Karmic.

---

### Post by greyfox1 on 2009-11-30
Hi Probable, I came across this thread while trying to resolve my issue, which was *exactly* like yours: Audigy 2 zs, card not listed in sound preferences, was working under Jaunty. I noticed that when I ran aplay -l, I got several errors related to my ~/asoundrc file. In my case, I still had this file from my Jaunty installtion (my ~ is located on a different partition that I just mounted again after re-installing the OS). 

I renamed my ~/.asoundrc file by issuing:

```
mv ~/.asoundrc ~/.asoundrc.bak
```

then logging out and back in. Presto! My sound card started working again. This makes sense, since I followed some directions or another to get PulseAudio working under Jaunty (maybe even Intrepid before that). I'm sure there were some configuration changes in Karmic related to PulseAudio, so I guess my tweaked conf file broke something.

I hope this works for you too! Maybe it will help the OP too.

---

### Post by Probable on 2009-12-01
Thanks for the reply! I actually got it working by completely uninstalling and then reinstalling ld10k. I actually installed it once, and the soundcard worked. Then I got my broadcom wifi ( bcm4318 ) working, and the Audigy disappeared again. A straight reinstall of ld10k did nothing, but completely removing it and installing it again did the trick.

Or maybe my karma just got better or something. Both the Audigy and the Broadcom seem to work or not work by rules distinct from the normal laws that govern the operation of computer components.

---

