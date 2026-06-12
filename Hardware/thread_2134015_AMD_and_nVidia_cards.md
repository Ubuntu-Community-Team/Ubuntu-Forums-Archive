---
title: "AMD and nVidia cards"
date: 2013-04-09
forum: Hardware
---

### Post by man_bash on 2013-04-09
Hi all

First off, I dual-boot with windows (insert boos and hisses).

My old nVidia 8800 GT died. I sent it for replacement under warranty to manufacturer who was foolish (and nice) enough to provide a life-long warranty on the card. In the meantime, I have found a great deal on a new AMD Radeon 7850 video card, with 3 AAA games that I was going to buy anyway, which made the card essentially "free", and I have no loyalty to either manufacturer whatsoever. Neither game runs in linux :(. In any case, I received a seemingly brand-new 9800GT 1 GB as a replacement for the 8800GT. So now I have both a 7850, which is a much better card for windows gaming (and the only other reason for a windows partition to exist, first being the stupid Canon printer), and a 9800GT, which, in theory, should get me more linux support. What I want to do is have both cards installed (I have a spare 16x PCIe slot at 4x-speed which is housing a 9500 GT loaner card from a friend at the moment), connected to the same monitor (the monitor has 3 inputs, 2 HDMI and 1 VGA, and will automatically switch to active input), and to have windows use the Radeon card, and the GeForce for linux. I think I'll use HDMI on the Radeon, and VGA on the GeForce (since it has a VGA port natively), and keep an HDMI cable available for my laptop (though it also has a VGA port as well as HDMI). The monitor is a 1080p panel. Power consumption is not a concern, and neither are the PSU capabilities. I just reinstalled Ubuntu, went with 13.04-x64 Beta, so no restricted drivers on linux system yet. I am already using both AMD (Radeon 7850) and nVidia (the aforementioned 9500 GT) cards on my windows system with no issues, so the question is what would I need to do to accomplish same in Ubuntu with the 9800 GT being the primary. My gut tells me to just install the latest nVidia blob from the repositories, and not install the fglrx at all as they seem to conflict with each other. Tell me if I'm wrong, and of any other issues I should be aware of. I do have a Steam account, and I do intend to run some games from there. 

Or am I just better off running Steam with the 7850 and selling the 9800 GT?

Thanks for reading all this and your input!

---

### Post by pdc on 2013-04-09
> first being the stupid Canon printer

..........could we sense from this that you are inferring that your Canon printer does not have linux drivers? Could you tell us the model number so that one can be sure of this

---

### Post by man_bash on 2013-04-09
> **pdc said:**
> ..........could we sense from this that you are inferring that your Canon printer does not have linux drivers? Could you tell us the model number so that one can be sure of this

It is a Pixma MP250, and, what do you know, it does have drivers available! Do you remember canon's "support" page for linux circa 2008 though? Given their stance then, I assumed they won't ever support linux. Humble pie, here I come!

In any case, the printer is hardly the grief for the amount of printing that I do... And not why this thread was made, either.

---

### Post by pdc on 2013-04-10
sure: your post was looking for video card support;

but from this link [http://support-asia.canon-asia.com/contents/ASIA/EN/0100236101.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100236101.html)

Canon supply both rpm and deb packages for your printer; in both 32bit and 64bit packages;

it was good of you to acknowledge all that; Canon; and Brother and Epson and HP are some of the printer makers giving very good linux support

---

### Post by CatKiller on 2013-04-10
Open-source drivers will potentially make both work. Installing proprietary drivers for one will stop the other doing anything useful. That was certainly my experience a few years ago. My inclination would be to try to get one card working in both Windows and Ubuntu and do something else with the other one since you aren't actually interested in using both at the same time; just one or the other.

There are people who've had lots of luck with the proprietary AMD drivers and others that have been burned by the Nvidia ones. Although it's potentially not as many as the other way round, it's worth a shot.

---

