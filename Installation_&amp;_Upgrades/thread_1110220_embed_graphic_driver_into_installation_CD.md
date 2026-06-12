---
title: "embed graphic driver into installation CD?"
date: 2009-03-29
forum: Installation &amp; Upgrades
---

### Post by shinew on 2009-03-29
Hi, I have a Geforce 9500 GT 512MB Dual DVI video card, and need to resintall Ubuntu 64-bit from scratch onto my new computer, as I have done this before with both the 64-bit & 32-bit, I could not continue with the installation(or boot the live CD) because after the initial "Ubuntu progress bar" has finished loading, the screen would just go blank. So I had to temporarily install with a old PCI graphic card , then install the correct driver for the 9500GT, which is really a hassle.

I'm wondering if any of the 2 options are possible and feasible(easier to do then swapping graphic cards):
1) "slipstream" the video card driver into the installation CD.
2) install ubuntu without the graphic card, in "text mode" if there is one. Because all I need is to be able to boot into the terminal, then I can just install the correct driver there.

thank you very much for your help!

---

### Post by Chemical Imbalance on 2009-03-29
[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)
[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by shinew on 2009-03-29
thanks for the quick reply & the link. I'm looking into it now.

---

### Post by shinew on 2009-03-29
hmmm... it seems to make a CD out of the "current" system. But I don't have the system setup yet...
I do have ubuntu running on my laptop, should I just try to install the desktop driver on to my laptop and make a live CD from it? Is it bad to slip stream all the laptop drivers into the installation CD for the desktop? it would be great if I could selectively choose the driver to embed. 
Also my laptop runs on ubuntu 32-bit, I would like to install 64-bit ubuntu for the desktop.

---

### Post by Chemical Imbalance on 2009-03-29
Why not just install onto the desktop then use remastersys?

Try booting the recovery kernel in grub then enter a root prompt.

---

### Post by shinew on 2009-03-29
> **Chemical Imbalance said:**
> Why not just install onto the desktop then use remastersys?

Try booting the recovery kernel in grub then enter a root prompt.

Because I don't have any linux distro installed on my desktop yet, only OS X. Can I boot into a liveCD without the graphic support? that would work I think.

---

### Post by Chemical Imbalance on 2009-03-29
If you can boot a livecd on your desktop, it will probably drop you to low-graphics mode, so it should work.

---

### Post by shinew on 2009-03-29
> **Chemical Imbalance said:**
> If you can boot a livecd on your desktop, it will probably drop you to low-graphics mode, so it should work.
Nah I can't boot with any graphic support(see my first post).

---

### Post by timjohn7 on 2009-03-30
> **shinew said:**
> Nah I can't boot with any graphic support(see my first post).

WHen you get to the 1st menu screen (using LiveCD), select Other Options (F6 I think).  Add "vga=792" at the end of the 1st line.
This should give you 1024 x 768 screen resolution which should work on any system post-1995 and enable you to get to apoint where you can install your requiresd drivers.

---

