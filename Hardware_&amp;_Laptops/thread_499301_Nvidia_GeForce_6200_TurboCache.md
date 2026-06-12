---
title: "Nvidia GeForce 6200 TurboCache"
date: 2007-07-12
forum: Hardware &amp; Laptops
---

### Post by werewolfzx8 on 2007-07-12
When ever I use Ubuntu for an extended amount of time, it seems to freeze up, and I must restart. I'm not sure what my motherboard is exactly, but I know it came from an HP a1245c. It has an integrated ATI Xpress graphics chip, and after my computer reboots from a freeze in Ubuntu, it immediately restarts AGAIN, but this time it's trying to use the ATI rather than my PCI Express card, which is an Nvidia GeForce 6200.

I am now using a set of drivers from a program I downloaded called Envy. For a while, it seemed to stop, but when I try to play 3D games, or play movies, or anything that deals with a lot of graphic card usage, it freezes again, and gives me the same problem as before.

If I give the card a good wiggle, then boot up again, it starts with teh PCI Express, rather then the integrated graphics [which is what I want], but it doesn't take long for Ubuntu to freeze up again.

I've already set the BIOS, and I'm almost certain it's not the video card it's self, because it works perfectly in Windows. I was thinking maybe if I replaced the motherboard, that could possibly fix the problem. If I get one without integrated graphics, then what does it have to switch to?

But I'm starting to get my doubts. I can't afford a new motherboard or video card right now... :(

[Using Ubuntu 7.04 FF]

---

### Post by EXCiD3 on 2007-07-12
You might need to configure /etc/X11/xorg.conf for both video cards. The problem could be that it is trying to use certain settings on the wrong video card. I am not sure how you would set this up and I really have no idea if this would even work, just a thought. Hope this helps! I know that having multiple monitors works this way and that multiple video cards might be closely related.

I would recommend just searching the forums for some help on other threads.... Sorry i can't help much more.

---

