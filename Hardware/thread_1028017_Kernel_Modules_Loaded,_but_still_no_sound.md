---
title: "Kernel Modules Loaded, but still no sound"
date: 2009-01-02
forum: Hardware
---

### Post by coolaj86 on 2009-01-02
lspci reports
00:0d.0 Multimedia audio controller: Trident Microsystems 4DWave DX (rev 02)

lsmod reports
snd_trident

aplay -l reports
no sound card detected

ALSA has supported this card for a very long time, it's at the top of the list of supported cards - with honerable mention of 'first cut' gpl code, but it seems to not be working anymore.

Hints?

---

### Post by prshah on 2009-01-02
> **coolaj86 said:**
> 
lsmod reports
snd_trident

Hints?

Did you recently upgrade the kernel? Was the sound muted at that time? I [ran into this problem]("http://ubuntuforums.org/showthread.php?t=995725") (though I'm not sure if it was because the sound was muted) and I could only solve it by upgrading the kernel when the new one was available (in the meantime, I used the older kernel entries from grub).

Note that this may not be your problem at all, especially if you have not performed a recent kernel update.

If you feel that this is indeed your problem, can you check if the sound works in an older (installed) kernel or the live CD?

---

### Post by coolaj86 on 2009-01-02
This is a machine that I once ran 5.10 on back in the day and I think it worked way back then. The sound card stopped working probably around 7.04. I'm not sure. But it doesn't work on the LiveCD either.

I opted for an easier solution. I posted on my local LUG asking about extra soundcards and today I'm going to go pick up a soundblaster card in exchange for some extra gadgetry of my own.

---

