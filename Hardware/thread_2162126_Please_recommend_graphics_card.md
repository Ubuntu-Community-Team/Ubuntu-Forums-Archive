---
title: "Please recommend graphics card"
date: 2013-07-13
forum: Hardware
---

### Post by bob-linux-user on 2013-07-13
I am running Ubuntu 12.04 64 bit on an Acer Aspire X1420 which dual boots with Windows 7 64 bit. When booting Ubuntu normally I find that the GUI does not start. I then select the previous kernel in GRUB and it boots up fine.

I am thinking this is a driver related problem and I am thinking of getting a new graphic card. This will need to be the PCI-16 express format as the computer is a relatively small form factor design. Also it only has a 220W PSU. I do not need the graphic card for gaming so I do not want an expensive one, just reliable.

Can anyone recommend one please?

---

### Post by TheFu on 2013-07-13
If the graphics works for any OS, just not Ubuntu, that means the hardware is fine and you most likely have a simple-to-correct driver issue. That's all.  **sudo lshw -C video** output would help.

If you just want a new GPU, for needs like yours, which are similar to mine, I buy a cheap nvidia GPU for $50 or less that is not under "legacy" support.  Something like a GT 440 would be my initial suggestion. Now you just need to find a version that fits your physical limitations AND whatever slots are actually on the motherboard. An article below says that the motherboard and online specifications do not agree in many places. You'll need to physically "look" at the slots and know what each is before deciding on a card.  Wikipedia does a great job explaining all the different PCI-whatever standards with photos and descriptions for every different slot type.

[http://www.sevenforums.com/graphic-cards/179797-will-graphics-card-work-my-computer.html](http://www.sevenforums.com/graphic-cards/179797-will-graphics-card-work-my-computer.html) says you have a plain PCI slot, the current GPU is integrated.  I don't know, but I'd be very certain you know exactly what is and isn't available for any new hardware.  I'd also check the BIOS to ensure you can disable the on-board GPU. Hopefully, that will save some power.

[http://www.tomshardware.com/forum/365660-33-graphics-card-acer-aspire-x1420](http://www.tomshardware.com/forum/365660-33-graphics-card-acer-aspire-x1420) is related too.

---

### Post by bob-linux-user on 2013-07-13
Thanks TheFu, I will look into it. I seem to be running ok on the slightly earlier kernel,  Linux 3.2.0-48-generic at the moment so I will see how that goes before taking any action. It also seems I need to open up the box and determine exactly what ports I have.

---

### Post by TheFu on 2013-07-13
I've had issues where the DKMS failed to rebuild and relink video drivers automatically after a new kernel was installed.  When that happens here, I force a reinstall using apt-get.

---

### Post by dannyboy79 on 2013-07-15
i am guessing it's just because you need to "reinstall" the nvidia drivers for the newer kernel BUT if you really want a new card, i recently got an nvidia 8400gs from newegg for about $50, it's PCIe. i am using the latest nvidia binaries from their website and it runs great. 319.32

---

