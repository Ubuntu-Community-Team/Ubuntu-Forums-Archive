---
title: "Installation will not go to partition manager screen."
date: 2011-11-23
forum: Hardware
---

### Post by Bebis on 2011-11-23
I have an Hp Mini 210 - 2200ev netbook that lately tried to install Linux on it.
While the live system boots and everything works well, if I try to do any installation (considering any debian based system) before Ubuntu 11.04 (for example NetUbuntu) the installation will get stuck on step (screen) before showing me the partition manager so I can choose. My disk was preformatted by HP. I tried to reformat it with an other linux distribution (based on another core) and everything went well. But the installation still does not get past this step. Depending on the exact distribution, it may pass the keyboard layout and then stuck.

The strange thing is that the installation program works without a problem even after it gets stuck, it responses if I choose to cancel the installation.

I searched for hours and did not found something similar so I would be very grateful if you could help me!

Ubuntu 11.04 and 11.10 installs without a problem. Also dmesg does not report something very special (I think).

---

### Post by jerrrys on 2011-11-23
sounds like you may already have four primary partitions

---

### Post by Bebis on 2011-11-23
I did had this thought too (or just that it had some extended partition and this was the reason why) and this is why I tried and formated the whole disk with the partition manager of another distribution but had no luck even after that. When I reformatted I deleted the whole partition table and created a single simple partition.

---

### Post by jerrrys on 2011-11-23
ok, if I understand you.  you have your hdd with one formated partition with nothing on it.  is that right?

---

### Post by Bebis on 2011-11-23
Yeah, correct.

---

### Post by jerrrys on 2011-11-23
i had to ask to make sure that no data was a risk.

fire up your ubuntu live cd and try without installing.

then open "gparted".  thats the ubuntu partition manager.

and delete the partition, then try an install.

---

### Post by Bebis on 2011-11-23
Everything is backed up safely. Though, I just reinstalled windows for the shake of having an OS to work with tomorrow. I will try the gparted way and tell you if I had any better luck tomorrow.

---

### Post by Bebis on 2011-11-23
I deleted the partition and still no response.

---

