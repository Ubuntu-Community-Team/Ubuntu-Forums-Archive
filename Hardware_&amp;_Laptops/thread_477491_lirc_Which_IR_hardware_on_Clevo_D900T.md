---
title: "lirc: Which IR hardware on Clevo D900T ?"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by emaxx on 2007-06-18
Hi all,

after having had a gentoo installation for approx. 3 years, which showed me a lot of the internals of a linux-system and was very, very fast, for convenienace-reasons i switched to feisty fawn a week ago, and i am very happy with it.

I m trying to get lirc running on my Clevo D900T laptop (which is identically to an "Alienware Area-51 M7700"), but don't have results until now.

I've got the module "lirc_sir" loaded, and also the lirc-daemon loads and doesn't comply, but irrecord doesnt show anything.

So my guess is, that i have to load a different module, or maybe specify some special hardware - i dont know.

Does anyboy know, which hardware is built into that laptop?
It was delivered with an "Avermedia tvphone98" remote control. 

BTW: when i press the "power" button on that remote, the KDE powerdown dialog pops up on my screen, even if the lirc daemon is not running. Exactly the same happens if i press the "power off" button which is located on the top-right side above the keyboard.

According to the daemon log, acpi receives a "powerdown" event in that moment. This is for sure due to some firmware functionality, which links the powerdown-signal from the remote directly to the powerdown-button mentioned above.

For me, that means, that the remote as well as the IR-receiver work well and has no hardware problems.

---

