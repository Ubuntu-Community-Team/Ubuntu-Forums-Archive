---
title: "Is there support for the ATI 4890?"
date: 2009-12-09
forum: Hardware
---

### Post by DeathOnJuice on 2009-12-09
I'm looking to build a new system very soon, and the 4890 seems to be far and away the best bang for the buck right now. However, last time I built one (several years ago) ATI had big compatibility problems. Is this still the case, or is the 4890 well-supported on the newest Ubuntu? What about on 64-bit?

If no to either of those questions, could someone suggest a roughly equivalent NVidia card?

---

### Post by Rohan Kapoor on 2009-12-09
ATI is still heavily unsupported in Ubuntu. I would personally buy an nVidia.

---

### Post by DeathOnJuice on 2009-12-09
K. On an entirely different note, I don't see why processors would be unsupported, but would I be OK with a Core i7 860 or a Core i5 750?

Also, is the GTX 260 a decent substitute for the 4890? Because the GTX 275 is more than $100 more. It's a shame the 4890 isn't supported; it's a golden deal.

---

### Post by cascade9 on 2009-12-10
You dont need ubuntu to support stuff for it to work. You can always install the 4890 manually. 

> - Grab the latest driver from ATI's website

- Open a terminal and move to the location where you saved the driver in:

 	Code:
 	cd /<location of driver> 
- Download needed dependancies:

 	Code:
 	sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms 



# install ia32-libs if on a 64bit system 
- Run the installer


 	Code:
 	sudo sh ati*.run 
- Let the installer finish, and when back in the terminal:


 	Code:
 	sudo aticonfig --initial 
- Reboot

Info from here- 

[http://www.overclock.net/linux-unix/503453-little-help-installing-4890-drivers-ubuntu.html](http://www.overclock.net/linux-unix/503453-little-help-installing-4890-drivers-ubuntu.html)

If I was after a new card, I'd be looking very ahrd at ATIs current offerings. In a lot of benchmarks the 4890 is faster than a GTX 275! 

BTW, CPUs arent something that get support. Chipsets are. You should have no issues with the i5 or i7 chipsets.

---

### Post by DeathOnJuice on 2009-12-18
So my new computer came in, and the build went well. I had a little smudge that I couldn't remove on the stock heatsink before I applied AS5, but I'm idling around 37C (can't check load temps because sensors aren't detected in Ubuntu :( ), so it should be all right.

However, I am having some problems with games, and I'm guessing it's the SAPPHIRE Vapor-X 4890. I installed the Catalysts drivers straight from ATI's site (by building Ubuntu packages first), but things are not running well. Portal was lagging mildly, which is much more than it should. Once I joined a game and got past the loading screen in TF2, the screen just flashes between all sorts of random distorted crap and repeats sounds like a broken record until I end the process. Similarly, WoW is good through the login screen, but then becomes one big graphical glitch.

I am hoping it is the card, just so I have the problem narrowed down. What do you think?

---

### Post by DeathOnJuice on 2009-12-19
So, I fixed the graphical glitches on WoW (the refresh rate was wrong and that was somehow causing it). Now, I'm getting decent framerates. Maybe, around 20, with frequent lag spikes down to practically 0. On lowest settings. In fact, this Core i7 860, 4GB RAM, and SAPPHIRE 4890 are performing roughly the same as my old system, which was a single core AMD 3800+, 1GB RAM, and an eVGA 7800GT, except that the resolution is higher (1920x1080 instead of 1280x1024).

If I could just get confirmation that this is probably my card's fault, it would be great. I don't want to send it back for nothing.

Also, TF2 can't be helped, as it doesn't even seem to have an option for refresh rate.

---

