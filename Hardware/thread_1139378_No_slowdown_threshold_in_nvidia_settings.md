---
title: "No slowdown threshold in nvidia settings?"
date: 2009-04-27
forum: Hardware
---

### Post by AllisonM on 2009-04-27
I'm running 9.04 on a Dell D630. MY video card is Nvidia Quadro NVS 135M, and I'm running it with the recommended driver, 180. 

My card is one of the defective Nvidia models, which means that it is more sensitive to temperature than it should be. I've already replaced it once and I'm not in the mood to wreck another in the near future. I'm not a gamer - the all I do is stream video, watch DVDs etc., so performance is not my priority.

My GPU is running hotter on Ubuntu than it does on Vista.  After about half an hour watching a video, I'm at about 69C in Vista and 75+ - up to something like 78 at times - in Ubuntu. Around 76 the fan goes on full blast, but it can't seem to get the temperature under control, and it stays at 77, 78 until I shut down the computer. I know none of this is apocalyptic, but it's making me nervous.

It looks like the Nvidia driver on Ubuntu isn't underclocking under any circumstances. "Slowdown threshold" is set to 0C, and it's grayed out. Even when I'm running hot, "performance" is always at 2. 

I'd like to set the slowdown threshold quite low, but I can't figure out how to. I've already tried launching nvidia-settings with administrative privileges - "slowdown threshold" is still grayed out. 

Help?

---

### Post by sinbad#1 on 2009-06-17
I have the same problem with my 8600m gt card except that my computer doesn't get hot enough to shut itself down. However it doesn't show a slow down threshold or the graph either but the core temperature is displayed.

---

### Post by newb85 on 2009-11-10
Same problem here.  nvidia 8200M.  Threshold is greyed out at 255.  My temperatures have exceeded 110C.  :(

---

