---
title: "How do I set/up use my PCI Graphix card as opposed to the one built in to motherboard"
date: 2006-08-09
forum: Hardware &amp; Laptops
---

### Post by DragonSoldier on 2006-08-09
Basically the thread name says it all, Ubuntu is great so far, I am still getting used to the transition, but I am catching on, just need to know how to get my RADEON 9800 128MB graphics card to work instead of the Intel extreme one on the motherboard.

---

### Post by bigken on 2006-08-09
in the bios you sould be able to dissable the on board graphics and in a 
terminal type sudo dpkg-reconfigure xserver-xorg and ati as your graphics
card ;)

---

### Post by DragonSoldier on 2006-08-09
Ok I got that but whenever I try to load it freezes on mounting hardware drivers or whatever. Did I do something wrong? Or do I have to download drivers? Pleez help...

---

### Post by Anduu on 2006-08-10
> **DragonSoldier said:**
> Ok I got that but whenever I try to load it freezes on mounting hardware drivers or whatever. Did I do something wrong? Or do I have to download drivers? Pleez help...

Give it some time...Liux may have to redetect/configure your new card

---

### Post by bigken on 2006-08-10
If this is a clean install and you have nothing to lose I would reinstall save myself the head scratching can you boot from the live cd

---

### Post by DragonSoldier on 2006-08-13
Ok I tried Re-insalling with my bios already set to boot my PCI graphix card, and it crashes brings up a bunch of command line and just stops. I made supper ate it, watched a 2 hour movie, and it never moved.

---

### Post by william_nbg on 2006-08-14
OK, I saw a similar problem recently. When you first turn the computer on, what do you see? Do you see a small info about your graphic card? Could be something's not set up right with your bios.

---

### Post by DragonSoldier on 2006-08-14
Well do you mean after bios? Because I see the hit del to enter set up window with the ACER logo in the background, then I see the boot screen to choose xp or ubuntu, so I pick ubuntu, then the ubuntu load screen comes up as per normal and freezes on that screen at hardware profiles. When I pop my live cd in and reboot, it will start the ubuntu load screen and then at like load hardware drivers it switches to a screen full of weird commands I don't know and then it freezes and doesn't go anywhere.

---

