---
title: "Booting Failure"
date: 2009-04-10
forum: Installation &amp; Upgrades
---

### Post by raeoh7 on 2009-04-10
Hi this is my first in Ubuntu Forums but i know that if i have a problem on ubuntu i should ask here. I tried to install ubuntu on my computer (shipped CD),  it did fairly well. As you see the loading before it boots, it starts to fill up (the first bar) then the (second Bar), etc, then at last FLASH! Then my monitor says "Going to Sleep", so I can't boot!
   But when i tried with Safe Mode It succefully worked, according to the information i found, my monitor or my VGA is the problem. First of all My monitor is HP PAVILION vf17, and my VGA is ATI Radeon 3850 256MB. Please, I was trying to figure this out for weeks. :(

---

### Post by iponeverything on 2009-04-10
Something to try. In safe mode go to 
"System -> Administration -> Hardware Drivers"

And see if there is a perpritory driver that you can enable for your video.

---

### Post by raeoh7 on 2009-04-10
> **iponeverything said:**
> Something to try. In safe mode go to 
"System -> Administration -> Hardware Drivers"

And see if there is a perpritory driver that you can enable for your video.

Do I go with an Safe mode? Then get a DRiver?

---

### Post by cariboo on 2009-04-10
Yes, your monitor isn't being detected properly, so start up in safe mode and make sure you have installed all the updates before installing the restricted video driver.

The reason the video driver is called restricted, is that is closed source, whereas the majority of the software Ubuntu uses is open source.

Jim

---

### Post by cariboo on 2009-04-11
If safe mode doesn't work for you I would suggest you start in recovery mode, select it from the grub boot menu, then at the menu select xfix, whe it is finshed, select resume and continue on to your desktop. Install all the updates, and then try System-->Administration-->Hardware Drivers to install the restricted graphics drivers.

Jim

---

