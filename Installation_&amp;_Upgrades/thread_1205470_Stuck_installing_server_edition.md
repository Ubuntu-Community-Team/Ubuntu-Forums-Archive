---
title: "Stuck installing server edition"
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by Wyvernoid on 2009-07-06
I'm installing Ubuntu Jaunty Server Edition to a VMware default setup, but the installation gets stuck in the "Configuring apt - Scanning mirrors" part. The progress first stayed at 43% for ten minutes or so, and then has been at 50% for about two hours. Right now it's still there - does anyone have an idea about what steps I should take to make it work? Thanks in advance!

---

### Post by jcarver on 2009-07-06
I am also stuck at 43% of Configuring apt - Scanning mirrors installing 8.04.2 Server edition..

Any ideas?

---

### Post by pndragon on 2009-07-07
I also need an answer to this.

I was trying to create a dual installation of WindowsXP/Xubuntu on an old eMachine with 2 hd that had for the most part outlived its usefulness (it only has 256 ram). The reason to try a dual install is to convince my wife that Ubuntu is Good (she's a Linux-phobe).

The first attempt was a liveCD. The install froze at ```
Configuring APT - 82%
Scanning mirrors...
``` and borked my grub. Since the the box was a gift, I don't have the Windows install disk to fix that, which bothers me not at all but irritates her no end.

Next I tried an alternate-cd. It reached
```
Configuring APT - 43%
Scanning mirrors...
```before freezing

What do I try next?

---

### Post by pndragon on 2009-07-09
I finally got xubuntu loaded by sideways through the [Ubuntu Mini CD]("https://help.ubuntu.com/community/Installation/MinimalCD") then these [Barebones Installation of Ubuntu instructions]("http://www.psychocats.net/ubuntu/minimal") and then opening a terminal and typing:```
sudo apt-get install xubuntu-desktop
```

--- Jim

---

