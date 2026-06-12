---
title: "Does the AMD Radeon R9 270 work with Ubuntu 14.04?"
date: 2014-09-14
forum: Hardware
---

### Post by Nate_Olander on 2014-09-14
I'm planning a PC build and this is a good GPU that provides plenty of power (more than the price-comparable NVIDIA GTX 750Ti) for my needs. It's also can be used in a Hackintosh, which I thought would be fun to do.

 However, the issue is, it's AMD. And, AMD doesn't have the best track record with GPU Linux support. Thus, I turned to the forums! I *did* read [this forum post]("http://ubuntuforums.org/showthread.php?t=2228550") about the same GPU, but it didn't have very many responses.

Does anyone have any experience with this card and/or heard of any results?

---

### Post by maxinstuff2 on 2014-09-15
I just did a build with the r9270x - it only works with the latest beta drivers from the amd website.

It was a PITA to be honest.

Works fine now - but if I could trade the time it took to figure out for an equivalent and compatible out of the box Nvidia card I would.

It involves editing grub settings and retrieving the xorg.conf file that the system inexplicably renames.

i can assure you it does work though and if you choose to get it I'll be happy to share the steps to get it right.
note that amd cards have known compatibility issues with certain games (not specific to linux or Ubuntu - they are just generally slow with updates)

---

### Post by Nate_Olander on 2014-09-16
Thanks for your input! Yeah, I'm probably going to be going with the GTX 750Ti because of NVIDIA drivers and all that jazz. Plus, I may still be able to hackintosh later; with the release of OS X Yosemite support for Maxwell Architecture GPUs should arrive in OS X.

---

