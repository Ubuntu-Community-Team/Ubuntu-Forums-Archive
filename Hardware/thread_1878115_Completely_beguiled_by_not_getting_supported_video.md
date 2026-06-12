---
title: "Completely beguiled by not getting supported video card to work!"
date: 2011-11-09
forum: Hardware
---

### Post by michaelveloz on 2011-11-09
This is an official call for help!! :-)

I have a system that's been running 10.04 for a while, It has an nVidia 7600 video card in it. I recently added a second video card, and nVidia GeForces 8400GS, which is listed as supported.

No matter what I try I can't get ubuntu to recognize this card.

ANY ideas at all would be greatly appreciated.

Notes:
1. If I dual boot to windows, it finds the 2nd card, installs the driver, and sets up dual monitoring; so I know the card is good, etc.
2. If I do a lspci, it shows the presence of the second adapter, and it just names it "nVidida", (not the more explicit name it gives to my first card like "nVidio 7600")
3. I've tried this:

sudo apt-get install nvidia-glx-185
sudo nvidia-xconfig
sudo service gdm restart

None of these seem to work and I'm at a loss for what the problem is..

Thanks
Michael

---

