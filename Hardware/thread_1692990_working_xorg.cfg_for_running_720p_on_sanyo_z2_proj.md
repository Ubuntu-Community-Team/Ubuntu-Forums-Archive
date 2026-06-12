---
title: "working xorg.cfg for running 720p on sanyo z2 projector?"
date: 2011-02-22
forum: Hardware
---

### Post by twinkiestar on 2011-02-22
I have a sanyo z2 projector (native resolution 1280x720) which doesn't seem to report to ubuntu its supported resolution completely, so ubuntu (or nvidia driver on a Nvidia 6200) doesn't allow give me option of 720p resolution from Administrator->"Monitor" configuration.  I was able to get the 1280x720 resolution when I run windows 7 on the same hardware and this projector, but the highest resolution z2 EDID report is 1024x768, I'm having a hard time to get 720p on ubuntu.  

can anyone share your working xorg.cfg that makes sanyo z2 projector shows 1280x720p on DVI connection?

so fyi, I have tried several modeline 
1) use CVT or GPT to create the modeline like (cvt 1280 720)
2) use modeline from internet reported
then I tried storing them in xorg.cfg, then reboot, or use xrandr to add the new modeline, neither works. the xorg.cfg reboot shows resolution fixed at 800x600, and xrandr --output option says **xrandr: Configure crtc 0 failed**

what troubles me most is the same nvidia card and z2 combo works well on windows, the ubuntu is supposedly more flexible but cannot get this to work....:(

---

