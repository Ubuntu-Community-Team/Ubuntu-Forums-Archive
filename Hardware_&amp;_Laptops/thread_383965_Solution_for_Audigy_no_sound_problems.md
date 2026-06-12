---
title: "Solution for Audigy no sound problems"
date: 2007-03-13
forum: Hardware &amp; Laptops
---

### Post by DoorGunner on 2007-03-13
Hi ....

If you have been having audigy no sound problems have a read. I have the same via8237 and audigy problems you and may people have had. (please subsitute via 82xx for you on board sound controller)

What i think is happening is Via and audigy are both competing for the job of sound controller. This has continued even though i turned my on board sound off at the bios level. The kernel still seems to recognizes that it is there. This is not good and seems to be the root of our troubles. You have noticed this too in your mixer with both via and audigy being available. Even sometimes audigy not even being available.

This is what I did to solve the problem

Quote:
sudo gedit /etc/modprobe.d/blacklist

add the following lines to the bottom of the file

#added to correct sound issues
blacklist snd-via82xx
What this does is prevent via82xx from ever being loaded into the modules on start..... ever. So someday if you take the audigy card out and want to use your via onboard sound you will just have to go back in and remove the lines.

After having done this you will note the next time you reboot you will only have audigy controlling kmix not via82xx. I have run this configuration for a while now and havnt had sound problems since.

---

