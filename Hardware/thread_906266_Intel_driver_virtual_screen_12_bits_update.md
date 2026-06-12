---
title: "Intel driver virtual screen 12 bits update"
date: 2008-08-31
forum: Hardware
---

### Post by Chillawowa on 2008-08-31
As the current vitual screen size of the intel GM965 (X3100) is limited to 2048x2048 pixels, it is not very useful when using two monitors which are larger than 1024x1024. However, most of the time the screens are larger, and then, their full size can not be used.

I believe i previously read in an ubuntu wiki article that it is a limitation of the driver used in older models (pre intel GM965) and that the buffer was limited to 11 bits. This means 2^11 = 2048 pixels.
However, the newer (GM965) cards have display buffers of 12 bits. This means that they should be able to display a virtual screen of 4096x4096.

When, where, how long and if will the extra hardware capabilities be implemented in a driver for linux? Is it already in linux kernel v2.6.27?

Thanks in advance for any info

---

### Post by gcranshaw on 2008-09-02
I have this exact same issue. I just tried to switch my work laptop over to Linux for the first time in the past few years. I was very surprised at how well everything worked with the 8.04 release. Only a few minor things to tweak. I am using a Dell D830 laptop with a docking station and two Dell 19" LCD monitors, one connected to the VGA port and one to the DVI port on the docking station. With some modifications to the xorg.conf file and using xrandr, I can get a display on both and it works fine with cloning the display. When I try to extend, I am limited to the 2048x2048 maximum. I use 1920x1200 for my resolution, but the limitation leaves me to 1024x768, not worth it at that resolution. I had to reformat and go back to WinXP. I did find a few posts and tried to recompile the xserver-xorg-video-intel and the mesa package, but the documentation and patch for the mesa package was not correct.

If there is any info on a good workaround, or an update to this driver allowing the 4096x4096 option, please post it. That is the only hurdle left for me, then I'm using Linux full time.

Thanks

---

