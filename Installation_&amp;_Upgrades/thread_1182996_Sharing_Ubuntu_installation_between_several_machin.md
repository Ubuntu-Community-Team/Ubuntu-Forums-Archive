---
title: "Sharing Ubuntu installation between several machines"
date: 2009-06-09
forum: Installation &amp; Upgrades
---

### Post by Bimme on 2009-06-09
Back in the university they used a system with SUN Sparc stations where most of the system files and home folders was stored on a server. The workstations also had a small storage for swapping and local hardware configuration etc.
This is at least what I think it was, the software where ran locally so it was not a thin client.

Is it possible to do a similar installation with Ubuntu?

My intention is to have a dual boot system with Ubuntu and Windows, but also being able to run the Ubuntu system from wmvare within windows. I have seen several solutions for doing this the other way (running windows from ubuntu) but not ubuntu from windows since it seem to lack hardware profiles.

I guess that e.g. the /etc folder should be duplicated on different partitions enable me to mount different system folders the correct places in /etc/fstab. But there is also a lot of configuration files that should be global. 

Ubuntu seem to have the /usr/local, /usr/local/etc etc as any other linux system, but they seem to be mostly empty. Is it supposed to be like that?

Or could it be that just the /boot folder should be different with different kernels depending on the hardware.

---

