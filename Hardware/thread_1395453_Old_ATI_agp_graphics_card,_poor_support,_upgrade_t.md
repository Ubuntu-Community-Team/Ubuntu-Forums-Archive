---
title: "Old ATI agp graphics card, poor support, upgrade to Nvdia?"
date: 2010-01-31
forum: Hardware
---

### Post by goosemold on 2010-01-31
I am trying to extend the life of my homebuilt rig which has an ASUS A7N8X-E Deluxe motherboard, unlocked mobile Athlon XP running at about 2.13 gigahertz, 1 gig RAM, Antec TruePower 380 Watt ATX12V power supply and, unfortunately it turns out, an ATI Radeon 9600 (AGP bus) graphics card.  The problem:  due to ATI’s lack of support for older video cards such as mine, it seems that I cannot run the latest distros which incorporate X-server 1.6, because there is no proprietary driver for these cards which is compatible with X-server 1.6.  (Please don’t urge me to use the open source ATI driver; I have found that it doesn’t meet my needs.  Also, I don’t want to have to try to roll back the kernel of a current distro.)

I want a rig with the latest kernel, and which continues to have reasonable graphics capabilities so I can run apps such as Google Earth which require 3D acceleration.  I don’t do a lot of gaming, though, so I figure I should be able to keep this machine running and meet my limited needs for years to come.  So I present a question for your consideration:  Because of its sorry Linux support for its “legacy” cards, I am thinking of abandoning ATI altogether henceforth.  But is there a low-cost, low-power Nvidia AGP card available that would enable me to keep upgrading my distros, have decent 2D and 3D capabilities, not overtax my Antec power supply, and maybe even improve performance of and extend the life of my machine?   

I apologize in advance if it seems that I am going over ground that may have been discussed elsewhere; however I am seeking advice that is specific to my particular hardware set-up.  Thanks for any help you can provide.

---

### Post by goosemold on 2010-02-02
I'm bumping this up in the hope that somebody will come to my aid.  Thanks!

---

### Post by Silent Warrior on 2010-02-02
The most straight-forward way I can think of is to get the latest/last working proprietary driver package from ATI and, well... work some source-code magic until it installs and runs under your system of choice. I don't know how to do any of that, though, but it should be doable - it's just a matter of what modules are loaded during boot-up, anyway, kernel be buggered.
Maybe you'll even have success with the official (legacy) ATI driver-download, though you might need to adapt the scripts?

---

### Post by ad_267 on 2010-02-02
I'm not sure what AGP cards are still available new from Nvidia, you might have to do a bit of searching or you could always get one second hand. I just built a new PC but was using an Nvidia 6600GT (AGP) before which was working fine (I have a 9600GT now). I had some issues running a couple of games (Penumbra and Enemy Territory: Quake Wars) but those seemed to be compatibility issues rather than a lack of power, and all other games worked fine.

---

