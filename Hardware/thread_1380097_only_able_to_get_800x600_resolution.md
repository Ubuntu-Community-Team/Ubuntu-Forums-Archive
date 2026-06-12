---
title: "only able to get 800x600 resolution"
date: 2010-01-13
forum: Hardware
---

### Post by Shea7993 on 2010-01-13
Hey, im having abit of a problem with no luck of solving =\

I installed a copy of ubuntu jaunty onto a HDD recently, and had a rather great resolution to work with, however now that I placed that HDD into another PC i only get 800x600 resolution max. However ive googled around and found other people have had the same issue with the same monitor I have, however im not too convinced it is the monitor, as ive mentioned before, when I first installed i had a great resolution to start with, and that was with the same monitor and neither PC has a graphic card, its all onboard. so I have tried numerous solutions ive found from increasing amount of available ram for graphics in BIOS, reconfiguring xserver (which seems to be more keyboard setup related than display?) to editing xorg.config (which shows me no monitor detected), none of which are getting me anywhere... So im rather frustrated, and looking for someone that could give me a proper solution and if possible an explanation of what went wrong?

PS. I probed my monitor by terminal command and from there my monitors resolutions and refreshrates were successfully displayed, so im guessing its detecting my monitor, however ubuntu just isnt doing it by itself... So its not my monitor thats the problem

Thanx for your time

---

### Post by bit mad on 2010-01-13
Try the **lspci** terminal command to see what brand of graphics it's got.
If it's Intel Graphics see :
[http://ubuntuforums.org/showpost.php?p=8386674&postcount=11](http://ubuntuforums.org/showpost.php?p=8386674&postcount=11)
- which gave me all I needed.

---

