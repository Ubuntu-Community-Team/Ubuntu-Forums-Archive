---
title: "Sis 650 Graphics Card"
date: 2009-05-19
forum: Hardware
---

### Post by markwilliams666 on 2009-05-19
I've put Ubuntu on my old desktop PC. 

The Graphics card (Sis 650) doesn't work though :sad:

Are drivers available for it?

---

### Post by Pretorean on 2009-05-19
vesa driver ?

---

### Post by markwilliams666 on 2009-05-20
Vesa driver? I don't understand what you mean

---

### Post by coffeecat on 2009-05-20
There is a driver for SiS graphics cards in the repositories, and it seems as though it's installed by default because I can see that it's installed on my system and my system hasn't been within a million miles of a SiS chipset. And it's going to stay that way!

The reason I say that is that unfortunately SiS is notoriously difficult in Linux. Some SiS chipsets simply refuse to work at all. I've no experience of SiS, so I don't know whether the SiS650 ought to work, or is one of the no-hopers.

So - our taciturn friend's suggestion of the vesa driver is a sensible one, albeit short on detail. The vesa video driver is a generic one which all graphics cards *should* work with. But you may only get fairly low resolutions, and you certainly won't get hardware acceleration. To enable the vesa driver you'll have to hand edit the /etc/X11/xorg.conf which without a GUI and if you're new to Linux, is going to be a little challenging. Not impossible though.

But first, post details of you hardware setup. Desktop or Laptop? Make? Model? Motherboard details? How much RAM? Which version of Ubuntu did you install? Did you use the desktop (live CD) or the alternate? If the desktop CD, did you get a GUI when running live? How did the installation go? When you boot up do you get anything? An error message or just a black screen?

---

### Post by Dennis Schulmeister on 2009-06-04
Hi Mark,

like it has been said SiS graphics on Linux is a difficult topic since SiS refuses to help the linux community in many ways. There are some official binary-only drivers form SiS but they are updated a bit seldom and don't support any 3D acceleration.

Maybe my wiki on that topic might give some insight: [http://ncc-1701a.homelinux.net/~linux-sis](http://ncc-1701a.homelinux.net/~linux-sis)

Let me know if you need advice or if you found something interesting out which could be added to the wiki.

Best,
Dennis

---

### Post by markwilliams666 on 2009-07-30
I can use the PC to do everything except play a 3D game or watch any kind of video file. I guess that's the best I'm going to get?

It's an old PC that I only use for office apps & surfing the net so it's no big deal really.

---

