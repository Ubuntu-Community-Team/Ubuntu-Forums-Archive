---
title: "New (used) graphics card won't boot OS"
date: 2019-03-08
forum: Hardware
---

### Post by MibunoOokami on 2019-03-08
Hi all,

This thread is directly related to [this one]("https://ubuntuforums.org/showthread.php?t=2413924") of mine, but since this is sort of a new problem I thought it best to start a new thread. If that was not appropriate, please feel free to merge them both.

Long story short, Ubuntu-Mate installed on Acer Aspire M1610 won't identify/change any other screen resolution than 600x480, xrandr and arandr didn't help, so I opted for the quickest option which was to buy a new (used) graphics card. The one I got is a 512Mb Gigabyte 9500GT which the person selling it said is compatible with my machine. So I've plugged in the card, moved the VGA cable to the new port, turned it on, get the splash screen (the one that says Acer and asks to press f12 for boot menu or del for BIOS) but once it tries to boot into the OS I get a distorted screen which won't do anything else.

I've been into BIOS and tried to find any settings to help me out, I tried disabling the On-board 1394 controller to no avail, and enabling the PCI/VGA palette snoop also to no avail. According to the seller all I should need to do is plug the card in and away you go. He also suggested unplugging the current one, I pointed out the machine only has a built in graphics card and that BIOS doesn't seem to have any other options than the ones mentioned above.

The how to found [here]("https://smallbusiness.chron.com/disable-onboard-graphics-card-bios-53738.html") was unhelpful beyond step 2/3 as I can't seem to find the option under step 4.

My basic question(s) is, can I get this card to work on my machine, or is this a compatibility issue despite the seller's (who seems to regularly sell parts) assurance? Thanks

ETA: disabling the on-board graphics controllers in Acer M1610 seems to be quite the issue with questionable solutions. One is to reinstall windoze with new controller plugged in, that apparently doesn't work. Another option if you have windoze is to disable the controller via windoze, also doesn't work. Two other options which may work, include resetting PRAM (which seems to be a Mac thing), or throwing some sort of physical switch on the motherboard, but no details of what the switch looks like or even where it is were provided. I don't know if this is helpful, it sounds like a lost cause, but since I've just spent money on the card, I would first like to try everything I can before going down the route of bringing old hardware back to life with cli commands.

---

### Post by MibunoOokami on 2019-03-09
I don't know what happened, when continuing to fiddle around with things, I ended up with an Ubuntu grub menu being displayed. This has never happened before, the system has always gone directly into Ubuntu-mate. After selecting Ubuntu from grub, all I got was a black screen. Decided one last time to try reinstall, Linuxlite again, don't know how or why, the graphics card allowed me to see the contents of the live-cd and then install it. The graphics card is now working fine so this problem is solved. 

Apologies to anyone looking for a specific solution to a similar problem, I don't have one.

---

