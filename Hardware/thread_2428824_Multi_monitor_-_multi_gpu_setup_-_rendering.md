---
title: "Multi monitor - multi gpu setup - rendering"
date: 2019-10-09
forum: Hardware
---

### Post by darkapha on 2019-10-09
Im having an issue with my setup and i dont know the correct  technical term to search for, so i'm trying to describe my problem as  best as i can.

  I have three monitors connected to two GPU's - 1st GPU is an Nvidia 2nd one is the intel iGPU build into the processor.
  Left Monitor (Intel) Middle monitor (nvidia proprietary) right  Monitor (intel). Ubuntu 19.04 automaticly sets up one big x screen with all three  monitors in it. I can maximize windows on all screens and they are  maximized to the screen they are currently on. I can drag windows from  screen to screen - that all works.

  But it seems the nvidia card has to do all the work. For example if im starting firefox and open up a youtube video, the  nvidia card decodes it although its displayed on a monitor connected to  the intel iGPU. I would like the nvidia gpu only do the work for the screen it's  connected to and have the intel iGPU only deal with all stuff that  happens on its screens.
  I dont know how to achieve this nor do i know the correct term to look for on the web.
  Thanks for your help :).

---

