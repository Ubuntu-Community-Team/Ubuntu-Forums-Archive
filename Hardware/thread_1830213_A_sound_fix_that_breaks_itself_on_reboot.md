---
title: "A sound fix that breaks itself on reboot"
date: 2011-08-21
forum: Hardware
---

### Post by dwigyit on 2011-08-21
Posted this in the general help forum but realized now that it probably belongs here (no wonder no-one replied :D )

I have an MSI GX660R laptop and the sound on it plays only out of the subwoofer (so it's quiet and can't go to the higher pitches without crackling).

There is a fix which I found on the internet (though it is for a slightly different model, as you can see in the comment [#] line), which involves adding this to alsa-base.config

```
#Fix for Intel (ICH9 Family) HD Audio Controller with Realtek ALC1200 on MSI GT725
options snd-hda-intel model=targa-dig
# targa-dig	Targa/MSI
# targa-2ch-dig	Targa/MSI with 2-channel
# targa-8ch-dig Targa/MSI with 8-channel (MSI GX620)
# Headphones
options snd slots=snd-hda-intel
alias snd-card-0 snd-hda-intel
```

Thing is, I can reboot the computer after adding it and it works perfectly - the speakers work fine and sound sounds great. But after one or two reboots (the number varies), sound stops working altogether and I have to remove the fix just to get the subwoofer-only sound again. Funnily enough though, I can add the fix back and reboot again and it works again for another reboot or two - it's very strange.

Anyone got any ideas? Thanks :)

---

