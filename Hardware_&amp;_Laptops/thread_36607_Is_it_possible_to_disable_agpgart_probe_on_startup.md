---
title: "Is it possible to disable agpgart probe on startup?"
date: 2005-05-24
forum: Hardware &amp; Laptops
---

### Post by ubuntuwow on 2005-05-24
I'm wondering if this is possible because I believe that the internal agpgart used by my integrated video card is interferring with my pci video card and causing x to crash on startup every time. My only solution is to remove the pci video card to get x to start. And, unfortunately my bios is bulls***, and I can not disable intergrated video which would probably fix my problem right there. My goal is just to somehow get ubuntu to boot with my pci video card in. hell, even if i had to disable a bunch of stuff to do it i would for right now.  any help or links that would help me would be greatly appreciated. 

Dell Dimension 2300 A02 BS Bios
1.80 ghz pentium 4
1 gb ram
nvidia GeForce 5500 pci
intel 845 integrated graphics agp

my xorg.conf file is currently configured with the drivers for the intel i810.

---

### Post by Ubuntu_User on 2005-08-31
Hope your problems are sorted- I came across your question while trying to do the same thing.

Most likely, your system starts both discover and hotplug as it boots. You need to disable both. To do this:

1. Edit /etc/discover.conf and add the line
[FONT=Courier New]skip agpgart[/FONT]

2. Edit /etc/hotplug/blacklist and add the line
[FONT=Courier New]agpgart[/FONT]

then restart your system. 

Unless you remove the automatic probe for agpgart in *both* these services, there is no way of killing the beast.

---

