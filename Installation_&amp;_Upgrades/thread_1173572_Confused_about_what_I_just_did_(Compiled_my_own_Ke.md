---
title: "Confused about what I just did (Compiled my own Kernel)"
date: 2009-05-29
forum: Installation &amp; Upgrades
---

### Post by mjwalfredo on 2009-05-29
I bought some more ram for my workstation to bring the total to 6GB up from 2GB recently and was sad to see that only 3.2GB was usable.  Well, I just used apt-get to install the source for my current kernel and then used make oldconfig + enable PAE (64GB) to compile the kernel so it would be able to take advantage of the new memory.

It seems to have worked pefectly, I installed the packages and rebooted. I now have 6GB of usable memory and my NVIDIA card seems to be working correctly with restricted drivers.  I am just a little confused because the guide I was using, [here]("https://help.ubuntu.com/community/Kernel/Compile"), made it sound like I would need to rebuild the linux restricted modules package since I use restricted modules...  Is this not the case?

---

