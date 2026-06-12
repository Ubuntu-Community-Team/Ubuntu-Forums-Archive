---
title: "Xorg memory grows and grows"
date: 2008-11-30
forum: General Help
---

### Post by fixitdude on 2008-11-30
Using "top" or "gkrellm" (a nice GUI memory / CPU monitor) you can watch memory grow when using Firefox and google maps with satellite mode turned on.

As you scroll around the satellite map, memory will grow but then you shut down firefox and it doesn't go away. (Yes, I used "ps x" and other programs to make sure it's not running).

This will continue until Xorg completely uses up memory and moves to using swap then you crash.

Only restarting Xorg will reduce memory usage, normally a reboot, which is a pain.

The (temporary I hope) solution to this is to not use google maps in satellite mode, it seems to be OK if you are careful.

I'm running a default install of Ubuntu gutsy 7.10 and the latest update of Xorg, it has been doing this for more then 6 months now. I didn't install any special nvidia drivers, they are whatever ubuntu picked.

Graphics: nVidia Corporation C51G [GeForce 6100]
KDE: 3.5.8

Anyone know any tricks to make Xorg dump it's unused memory, or compact it or whatever without a restart?

And if you are running Hardy 8.04 does it still do this? (I don't have time right now for all the problems upgrading always throws at you)

---

