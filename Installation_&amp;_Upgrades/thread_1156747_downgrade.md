---
title: "downgrade"
date: 2009-05-12
forum: Installation &amp; Upgrades
---

### Post by Messyhair42 on 2009-05-12
I've been having lots of little problems with Jaunty, mostly with disk latency and it's just too much (could also be a problem with my hardware but i see it as unlikely). rather than change this with a completely different OS i want to downgrade to Intrepid or Heron but i'm not sure which one. i do plan on upgrading to Karmic when it comes out so i'm more inclined to go with Intrepid since i dont need LTS until then. I got into Ubuntu using Intrepid and never had the problem. the way i have my computer set up now is a 1TB HD with jaunty, /, /usr, /var, /tmp, and /home are different partitions, all ext3, swap is separate as well. and a 160 GB HD with Intrepid on it (i was going to keep it around until i got my jaunty problems worked out) i know i could use this as my primary version, i just would rather have everything on the big drive (two weeks with Jaunty and the TB is already 1/3 full)
so in order to downgrade i would boot to a liveCD and then how would i format the partitions? common sense tells me to leave /home alone ('90's movie reference, could i make a linux joke out of that?) and just reinstall / since it contains /root, /bin, /sbin, /lib, and /dev (/boot is where?)
lastly which version should i go with, i had good luck with Intrepid (is it possible to have the same version more than once on the machine...on different HD's?) or does Hardy have better hardware support?

---

### Post by Messyhair42 on 2009-05-12
i can't even do anything in Jaunty anymore, what would be the correct way to overwrite the OS with an older version of ubuntu? is it possible to keep all my files in /home?

---

### Post by SunnyRabbiera on 2009-05-12
This is why most older use4rs set a seperate /home partition, so that the files in the home directory dont get messed up when updating

---

### Post by acmariner99 on 2009-05-12
I would suggest overwriting jaunty with the version you had the most success with until you decide to upgrade to something else. (As you said, jaunty cant do anything,so it is just taking up space.) Use the live CD of the distro you want and install to jaunty's partition.

---

### Post by Messyhair42 on 2009-05-12
so because i have 5 partitions +swap which ones need to be formatted with the new installation?

---

### Post by Messyhair42 on 2009-05-13
bumping, i'd like my last question answered b/c i'm installing today

---

### Post by Messyhair42 on 2009-05-13
I'm trying to backup documents i've modified or created since the Jaunty install, and i'm doing it all from Intrepid on another disk. I can mount the disk once, but soon after i get input/output error and cant copy anything. if i unmount it it wont let me remount it. is this because the disk is bad or because of the funky Jaunty install on it? if i want anything off of it at all i'm going to have to be able to get Jaunty running and copy from there. or could a new install fix this.

---

