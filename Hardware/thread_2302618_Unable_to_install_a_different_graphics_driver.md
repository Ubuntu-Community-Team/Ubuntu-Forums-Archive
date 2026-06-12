---
title: "Unable to install a different graphics driver"
date: 2015-11-11
forum: Hardware
---

### Post by mikecole on 2015-11-11
I have an NVIDIA GeForce 650 card, and the DVI port on the left seems to have started having problems.  I say this because when I have a monitor plugged in to it, it'll boot and show splash and loading pages, but when the machine finally boots all the way, I have a black screen with a cursor blinking in the top left, about 4 inches in from the left side.  If I have both monitors plugged in (both on DVI, the card has 2 DVI ports and a mini-HDMI) then the monitor on the second DVI port displays fine after boot, and Ubuntu shows no other monitor connected.  

I have switched the BIOS settings to allow both the internal graphics (Intel based graphics) and the GeForce card to run, and plugged on monitor into the onboard graphics and the second into the working port on GeForce card, and I boot.  I have have mirrored monitors, but when I try to set them to be independent, I get a stretched desktop that looks FUGLY and is unusable in any meaningful way.  

The graphics driver is still set to an NVIDIA driver, and I tried to change it to Xorg, but it'll go through the steps when I hit apply, shows the little orange progress bar, and then returns to the previous driver.  It does this when trying to switch to a newer (and tested) NVIDIA driver as well.  

I'm at a loss.  The best I can determine is that the first port on the NVIDIA card is damaged.  When connecting the new monitor earlier there was a static discharge between the DVI port on the monitor and the cable, and I believe that tiny little bit of juice caused damage to the card.  

Does anyone have any brilliant suggestions, short of replacing the graphics card, on how I might be able to get this thing working in a dual monitor mode that's productive and useful (not mirroring or stretched) so I can get back to work and stop futzing with this silly thing?

---

