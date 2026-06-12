---
title: "HP Laptop and SSD..Win 7 or Ubuntu"
date: 2014-09-17
forum: Hardware
---

### Post by Nick_Brennan on 2014-09-17
Hi everyone. New to the forums. I have an older HP Laptop, a 6910, and I wanted to use my Samsung 840 Pro SSD with it. But I don't know if I should put Ubuntu on it or Win 7. What would be faster? I know asking that question on a linux forum is self abusing but I always thought Win 7 would be faster due to it natively supporting ssd's better. Talking out of my ass on that one. Is there special versions of Ubuntu that are stripped down for laptops? I'd just like to get this thing running with my ssd and need help.

Thanks! :)

---

### Post by oldfred on 2014-09-17
It depends a lot on laptop specs. And if too old it may not have AHCI in BIOS and for trim to work with SSD you must have AHCI on.
I had to turn AHCI on in desktop and then XP stopped working, so I finally stopped using Windows. :) Windows 7 does have AHCI drivers but early installs did not include them by default.

But issue is how fast operating system is and then the desktop or gui on top of that. With Linux you have many different desktops and some are heavier or full functioned but need better hardware and particularly better video card/chip. Ubuntu & Kubuntu need newer or better hardware to run well, but any system that runs Windows 7 well should also run them. But older systems can run Xubuntu or Lubuntu which are much lighter weight desktop gui.

My laptop is from 2006 and has 1.5GB of RAM with default Intel chip for video. It did not run 12.04 with Unity, but I installed fallback/flashback/gnome-panel or whatever its name is which is the gnome2 look alike. That runs well on laptop with full Ubuntu. I do have 64bit installed but if I load more than one large app with a couple small apps then it uses swap and gets slow. But I wanted same configuration as my desktop. Desktop is part 2006 & part 2009 with a small SSD added a couple of years ago. It flys with Ubuntu/gnome-panel and runs Unity fine, I just do not prefer Unity.

---

### Post by rolkin on 2014-09-17
If your only concern is native sdd support, then all the newer version of Ubuntu have auto-trim support by default. I've actually felt more comfortable running linux (Arch) on my laptop with an ssd because I know exactly what and when it's performing the proper ssd maintenance.

---

