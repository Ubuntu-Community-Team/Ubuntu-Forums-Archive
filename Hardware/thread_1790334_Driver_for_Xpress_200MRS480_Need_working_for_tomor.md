---
title: "Driver for Xpress 200M/RS480? Need working for tomorrow!"
date: 2011-06-24
forum: Hardware
---

### Post by amp_man on 2011-06-24
I've just installed Ubuntu 11.04 on my old HP ze2000 (my regular laptop had to be shipped in for service). I need to have this running for tomorrow, for a couple service calls. After the initial install, I'm not sure what driver was being used (edit: Gallium3d/r300g from what I understand), but Unity's top and side bars were completely illegible and grainy. I apt-get update'd and installed fglrx, but now it's defaulting to a VGA driver. What driver should I use to get this working properly?

---

### Post by amp_man on 2011-06-24
Alright, not as important anymore, found info on Unity-2d and gave it a shot, it's working fine, and will do what I need it to (let me look at service manuals). It would be nice to have 3d Unity working, but not nearly as critical.

---

### Post by scradock on 2011-06-24
> **amp_man said:**
> I've just installed Ubuntu 11.04 on my old HP ze2000 (my regular laptop had to be shipped in for service). I need to have this running for tomorrow, for a couple service calls. After the initial install, I'm not sure what driver was being used (edit: Gallium3d/r300g from what I understand), but Unity's top and side bars were completely illegible and grainy. I apt-get update'd and installed fglrx, but now it's defaulting to a VGA driver. What driver should I use to get this working properly?
I have a zv6000 with the same sort of video chipset (200M 5955) and am having no problems with compiz and Unity(3d) in Natty or Oneiric. I use the open-source drivers, xserver-xorg-video-radeon and x-x-video-ati. I haven't been able to use fglrx for a while, since the last-but-2 upgarde of xorg, if I remember correctly. However, the open source drivers do just fine.

HTH

---

