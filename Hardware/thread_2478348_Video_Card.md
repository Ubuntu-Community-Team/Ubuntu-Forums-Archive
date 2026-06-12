---
title: "Video Card"
date: 2022-08-23
forum: Hardware
---

### Post by sanman770 on 2022-08-23
Does Ubuntu work well with Radeon?  If so is there a recommendation for a card?

---

### Post by TheFu on 2022-08-24
AMD makes many GPUs for different needs. "What video card" without any statement for the purpose, planned uses, budget, won't get you specific recommendations. AMD drivers are shipped with the kernel.  Just avoid really new hardware and really old hardware. If you buy last year's card in your budget range which matches the use, it should be fine.
Obviously, you'll need to run a current release of Ubuntu for this to happen.  22.04 is it now.  If you want to run 20.04, then perhaps a 2 yr old GPU would be better?

Not all Radeon GPUs are created equal.  AMD has used that name for at least a decade, so I wouldn't buy one over 3 yrs old, though it would still likely work.  I know that my AMD E-350 APU with Radeon graphics lost support around 2014.  For $100, it was an impressive media player system at the time thanks to good driver support for mpeg2 and h.264 video.

To get driver/GPU decoding support for h.265 video, I fear you'll need a $150-$300 GPU now.  For encoding h.265, that's likely a $200-$1000 GPU - or just let the CPU do encoding.  If you don't care about video playback, this can be ignored.

If you game a little, you'll probably need to spend more.  Whereas I don't game on Linux at all, so for me, video playback is the main driver for any GPU.  Some of my systems don't need any GPU. They are accessed only over the network 99.999999% of the time.

Last fall, I got a Ryzen 5600G which has a capable GPU on the CPU. At the time, a cheap GPU was over $100, so getting the on-board GPU was to save costs. The fact that the AMD on-board GPU was more capable than an nvidia GT 1030 was a bonus.  Drivers for the 5600G iGPU weren't added until kernel 5.10.x and later. The system runs 18.04 which had a 4.15.x kernel at the time.  The GPU worked, but with F/LOSS GPU drivers, not AMDs drivers.  That meant the video was a bit slower, supported resolutions were lower, and video playback had tearing.  I don't think audio worked at all, but I don't really remember.  The only solution to get better GPU support was to run a newer kernel, which I did and that system is working nicely.

---

### Post by sanman770 on 2022-08-24
TheFu Thank you so much.  You've answered my question quite thoroughly. I'm not going to run 22.04 just yet.  I like to extend new OS's with a 6 month grace period.  I have 20.04 and it works great.  Thanks again.

---

### Post by TheFu on 2022-08-24
> **sanman770 said:**
> TheFu Thank you so much.  You've answered my question quite thoroughly. I'm not going to run 22.04 just yet.  I like to extend new OS's with a 6 month grace period.  I have 20.04 and it works great.  Thanks again.

I'm with you, but even more cautious.  I have a few 22.04.1 play VMs running, but nothing I'd call "production".  No any servers and definitely not any desktops.  Just toy systems to learn what's been broken. There's always something broken in a new release that impacts my systems. Always.

---

### Post by mIk3_08 on 2022-08-25
> **sanman770 said:**
> Does Ubuntu work well with Radeon?  If so is there a recommendation for a card? 
In my case AMD Radeon video card works well in most of my Linux Ubuntu system. I haven't encounter any errors using AMD graphics cards with Linux Ubuntu Operating System installed in my two hardware desktop machine. So far so Good. Regards and cheers.

---

