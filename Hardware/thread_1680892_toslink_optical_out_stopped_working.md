---
title: "toslink optical out stopped working"
date: 2011-02-03
forum: Hardware
---

### Post by johnrunsubntlnx on 2011-02-03
my mobo has a toslink optical out as well as the standard 3.5 audio out.  the way I have my setup is, i have the 3.5 audio out connected to my speakers and the toslink out connected to an external dac/amp which is then connected to my headphones

everything works well a few days ago.  but for some reason, when I tried it last night, the toslink optical is no longer sending audio out

i tested my toslink cable, not a problem.  tested my external dac, also not a problem.  toslink jack behind my pc has that red light to it so I'm assuming jack is not a problem



i guess it all comes down to ubuntu not sending out audio through my toslink


i'm not familiar with how sound is processed on ubuntu.  can you guys give me some troubleshooting tips?  things I could poke at and look into?  stuff like bad settings, compatibilities, drivers, etc..


I didn't make any major changes recently except for a kernel update


thanks




/edit

I had my wife boot into an older kernel and test the toslink audio and it's working flawlessly

what items do I have to check from my older kernel and make sure that the newer kernel has?

I know my nvidia driver stopped working during the kernel update and I had just recently fixed this

maybe the toslink driver is suffering from the same effect?  also how can i check my other drivers to make sure they're working the same way they were with the older kernel?


thanks




/edit again

I did some research and it seems like I'm getting the same exact problem as this guy:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/711598](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/711598)

same problem, same 64-bit 10.10, same -24 and -25 kernels

although I do have a different mobo :D

---

### Post by cchhrriiss121212 on 2011-02-03
Kernel updates can occasionally knock out hardware functionality. If you put aplay -l ionto a terminal you can see what audio chipset you have, possibly it is the same one that is in that bug report. The easiest solution would be to use the older kernel, unless you need the new one for some reason?

---

### Post by johnrunsubntlnx on 2011-02-05
that's what I did for now, set my previous kernel as the grub default

i'll wait till a bit I bet a lot of other people are experiencing this too

thanks

---

