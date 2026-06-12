---
title: "Sli?"
date: 2007-06-15
forum: Hardware &amp; Laptops
---

### Post by numberboy on 2007-06-15
Hey,
I've got two 7900GTs on an ASUS SLI-capable motherboard, and I was wondering if it's possible to turn on SLI somehow. nvidia-settings shows both GPUs as being there, but the second doesn't have any options. When I googled this, I found some screenshots of nvidia-settings with an option to turn on SLI, but they were all from last year, and the nvidia-settings that I've got doesn't contain such settings.

I use Cedega so it'd be quite nice to not have my other card sitting there doing nothing. Any help'd be appreciated.

Edit - Also, I've got another hardware issue, so I may as well ask here;
My machine has onboard AC'97 audio, but under Windows I noticed some interference with the mic socket, so I put in a spare Creative Audigy I had and used that. Problem is, now I've installed Ubuntu, it seems to choose at random which to use for sound when it boots. To make matters worse, GNOME's volume control widget also seems to select randomly which device's audio to control, and more often than not goes with the wrong one. In Windows I went into Device Manager and just disabled the onboard; is there a way to do this in Ubuntu?

Running Ubuntu Studio 7.04, by the way.

---

### Post by reset3x on 2007-06-16
Hey numberboy!!! Looks like we have the same setup... I have the AN832SLI Deluxe and two 7900 GT KO's running in SLi.... If you have the nVidia drivers installed you can do sudo nvidia-xconfig  --sli=yes .... in the Terminal... When you go into the nvidia control app you'll see there are a couple of more options now... like the HUD which lets you monitor sli load balancing when you're using a compatable app. ie: games ;)

If you want to disable your onboard sound you'll need to go into your bios and then find onboard periferals and change it from auto to disable... That should get you going!!

Good luck!!!

---

