---
title: "Is &quot;Creative Sound Blaster 5.1 VX&quot; working fine?"
date: 2015-03-16
forum: Hardware
---

### Post by mina2 on 2015-03-16
Hi.

I'm about to get me a Sound Blaster 5.1 vx (coz that integrated in the G1Sniper motherboards, core3d, is so weakly supported so far :cry::cry::cry::cry:). I can't get JACK working with it and probably I won't for quite some time.

Anyway, anyone has a sound blaster 5.1 vx? Is it working fine? Drivers to get from somewhere? Issues? Anything?
...Or maybe anyone that *doesn't necessarily have it *but can confirm it works?

Thanks!! ;)    *my first post *:lolflag:

---

### Post by JDorfler on 2015-03-16
You should check to see if the sound chip is on the [Alsa Matrix]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Creative_Labs").  I am pretty sure it is not support fully yet.

---

### Post by Yellow Pasque on 2015-03-16
Supposedly, it's supported:
[https://github.com/torvalds/linux/blob/master/sound/pci/ca0106/ca0106_main.c#L242](https://github.com/torvalds/linux/blob/master/sound/pci/ca0106/ca0106_main.c#L242)

---

### Post by mina2 on 2015-03-24
Well I got the card. Audio's working extremely fine, though it needed a little tweak at first, the right speakers were silent. Just had to turn up the levels from alsamixer. ...Microphone not working so far :( I don't know if there's a solution. 

I made a petition for the core3d thing [https://www.change.org/p/creative-technology-do-linux-drivers-for-your-sound-cards](https://www.change.org/p/creative-technology-do-linux-drivers-for-your-sound-cards) This lack of drivers issue is so daunting.

---

