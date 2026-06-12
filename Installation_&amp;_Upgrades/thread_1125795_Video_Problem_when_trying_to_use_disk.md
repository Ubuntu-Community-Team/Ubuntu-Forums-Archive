---
title: "Video Problem when trying to use disk"
date: 2009-04-14
forum: Installation &amp; Upgrades
---

### Post by Buntonw on 2009-04-14
I am new to Ubuntu and I am wanting to install it on my desktop:

Asus M2N-SLI Deluxe (ubuntu compatible)
Nvidia 7900GT (not ubuntu compatible)
4gigs corsair xms ram
amd64 3.0GHz

As you can see from my specs my video card is not ubuntu compatible, I found that out when I checked the hardware compatibility page for nvidia cards.

My problem is that whenever I try to either boot off the Live CD it will load the initial Live Menu, but if I choose to boot off the Live CD or to install all that happens is it freezes on a screen with random vertical lines that resembles when a display cable goes bad or you bust an LCD.

From this point I can hit my power button and ubuntu will back out to the shut down screen when it ejects the disk and says to press Enter to shut down, and this screen is fine, it's strictly on the screen past the menu that I get crazy lines.

What I'm wondering is, perhaps it's not freezing, but just sitting on a menu and I can't see it because of the lines, giving the impression of freezing.  If that video card won't work, wouldn't it just use the video off my motherboard which is ubuntu compatible?

---

### Post by upchucky on 2009-04-14
if booting with the live cd gets a graphical display then an installed ubuntu can also get a graphical display.

you can look at the xorg.conf that the live cd uses when it boots, use those settings for the xorg.conf when ubuntu gets you as far as a command line upon install.

if ubuntu will not boot to a graphical display using the live cd, take out the nvidia card, then you may need to go into the bios to enable your onboard graphics.

if you do not know how to get into the bios, google the machine mainboard about how to get into bios.

---

### Post by Mark Phelps on 2009-04-15
Guess I must be missing something ... you say that (1) you KNOW your video card is NOT Ubuntu-compatible, and (2) you tried using Ubuntu with the LiveCD and can't get decent video.

If you do succeed in forcing an install, you most likely will not get a desktop and be relegated to command line only activities.

Is that really what you want to do?

---

