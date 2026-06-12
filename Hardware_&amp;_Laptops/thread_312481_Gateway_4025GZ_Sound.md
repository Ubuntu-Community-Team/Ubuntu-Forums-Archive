---
title: "Gateway 4025GZ Sound"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by jgrimm on 2006-12-04
Hey folks!

I hope I'm posting this in the right place (and I certainly hope I'm asking the right question) - I am relatively new to the administration side of Linux, and could use a hand. 

Searching has offered possible solutions, and I've tried just about everything I've found so far (esp. the items in the Comprehensive Sound posting) - but thus far, I have no luck in getting the sound to fire up on this laptop.  Everything else works great; just the sound seems not to be functional in the least.

I'm running Kubuntu Edgy; the installation seems to have merrily found the soundcard:

```

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0



```

Perfectly happy.  Running alsamixer shows everything seems to be on - I have muted the 'external amplifier' channel as suggested by another thread, but I get nothing either way.  

What else might I be missing?  Drivers seem to be in, it seems to be recognizing the card, and all my channels are up - but no sound from anything at all.

Thanks in advance, folks - I /really/ appreciate it.

---

### Post by jgrimm on 2006-12-04
HA!  Got it!  For those that may be interested, the issue may be more generic than just the Gateway:

The trouble was in AlsaMixer.  It wasn't that anything was muted, but the headphone jack detect and line in detect were both on.  Turning both of those off fixed the problem.

Apparently, the auto-detect routines (line-in) turns everything off - and the system still detects me plugging in headphones, all works well.   So, make sure you've got those toggles off or nothing else really ends up mattering.

---

### Post by zo3adams on 2006-12-16
Thanks for posting your solution, For what it's worth this was also the fix on Gateways M320E laptop.

---

### Post by breaking on 2008-02-04
Where do you turn on/off the headphone and line in jack detection? I've got alsa mixer open on my 4025gz and don't see any such options (just installed ubuntu today, so i'm a total noob...treat me like a toddler if you've got an answer)

edit: nevermind, i found it, heh. thanks for this post though, i had to toggle headphone sense on and then off and started working

---

