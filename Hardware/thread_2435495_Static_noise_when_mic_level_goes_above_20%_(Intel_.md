---
title: "Static noise when mic level goes above 20% (Intel chipset)"
date: 2020-01-21
forum: Hardware
---

### Post by kent-3 on 2020-01-21
Kubuntu 18.04.3 on a Thinkpad X1 Carbon 6th Gen (Intel chipset).

I'm having a problem where the mic is producing static on the line (it's not background noise) any time the mic level goes above 20%. I've already gone through other threads to discover how to turn off the mic gain, which is how I was at least able to get to the point that I can use the mic without static on a VOIP call (manually setting the mic level to 18%). The problem is that some programs auto adjust the level for e.g. a Google Voice call, and that keeping the mic at 18% means the volume isn't really loud enough for the person on the other end of a call. 

The shift from silence to static happens quite dramatically. At 18% it's silent; at 20% I start to hear a few pops; at 22% it's full blown white noise.

Is there any hope for solving this? Or is it down to a buggy Intel driver?

---

### Post by CatKiller on 2020-01-21
It's possible that it's autodetected the wrong control for the mic gain. Many audio devices have a separate pre-amp (sometimes called something like "boost"), which is often noisy.

You could have a poke around in alsamixer to see if that's likely to be the case.

---

### Post by kent-3 on 2020-01-21
> **CatKiller said:**
> It's possible that it's autodetected the wrong control for the mic gain. Many audio devices have a separate pre-amp (sometimes called something like "boost"), which is often noisy.

You could have a poke around in alsamixer to see if that's likely to be the case.

Thanks for your reply. 

It was in alsamixer that I found (by using F5 and going all the way to the right) and disabled (set to 0) the "Internal Mic Boost", which allowed me to get silence if the level is below 20%. With it on at all (the default) I get pure crazy static. I've also set the line labeled "Mic Boost" to zero, though in my tests that level doesn't seem to do anything. 

In alsamixer it shows the chip as Realtek ALC285, for what that's worth.

---

### Post by kent-3 on 2020-01-23
Can anyone provide further insight? Or should I be posting this elsewhere, or filing a bug report somewhere?

---

### Post by kent-3 on 2020-01-27
Please?

---

### Post by CatKiller on 2020-01-27
> **kent-3 said:**
> In alsamixer it shows the chip as Realtek ALC285, for what that's worth.

I did find various solutions that people had come up with for quirks with that chip's mic input when I searched, but I generally browse from my phone so I wasn't able to pick through them all to find a solution that matched your symptoms. 

It does seem that the ALSA project aren't yet aware of all the quirks that manufacturers have introduced when they use that chip. You might be able to find a solution that works for you, and you might be able to provide useful information to the ALSA project to prevent other users from hitting the same problem. All of the sound hardware I've used with Linux was already fully supported by ALSA, so it's not a process I've gone through myself.

---

### Post by kent-3 on 2020-01-29
> **CatKiller said:**
> I did find various solutions that people had come up with for quirks with that chip's mic input when I searched, but I generally browse from my phone so I wasn't able to pick through them all to find a solution that matched your symptoms. 

It does seem that the ALSA project aren't yet aware of all the quirks that manufacturers have introduced when they use that chip. You might be able to find a solution that works for you, and you might be able to provide useful information to the ALSA project to prevent other users from hitting the same problem. All of the sound hardware I've used with Linux was already fully supported by ALSA, so it's not a process I've gone through myself.

Thanks again for your input. I was able to fix the problem by upgrading to a 5.4 kernel (had been running a 5.0 kernel). I had been hesitant to upgrade because a recent kernel upgrade had killed Wi-Fi.

---

