---
title: "How can I use Xrandr (cvt) to set a 4K --output from (Monitor) HDMI--into CPU DVI-O"
date: 2017-06-04
forum: Hardware
---

### Post by whereismymindat2 on 2017-06-04
How can I use Xrandr (cvt) to set a 4K --output from (Monitor)HDMI--into CPU DVI-O...I tried cvt with 4K settings, won't work. What HZ should I use?...HDMI (NOT "smartTV"--just "A T.V."/Monitor).Toshiba 40U 1400LI have 2-Video Chips----INtel and AMD/ATI RADEON....Interestingly. Trying to install the deb package for AMDgpu----it looses ability to "SEE" my Toshshiba (40L 1400U)--Ubuntu "SEE'S" it "natively" but gets it wrong. (72"). Won't let me go above 1980x1080/60hz I can modeline a few High Res, but must be missing something. as when I go to set it....I get "No Video"Also, I have a problem where Boarders not respected (snap)--Gridline----it takes typical Gedit window about 80% before it realizes a "snap back" to grid..which is *SEEABLE* to me.,thanks in advance.I'm on a 16.04.2 distro, not sure how to change that in Panel.

---

### Post by him610 on 2017-06-05
Hello lost_your_mind,

This is not to address your issue, but to suggest how you may get someone to respond to it.

State your problem in clear concise language.

Provide some information on your system. In your case, the GFXcard, your monitor, and your operating system.

Suggested terminal commands that will display information about your system:

```
inxi -SMCG

hwinfo --monitor

hwinfo --gfxcard

xrandr 
```

In a new reply, use copy_and_paste to place the response of each command within code tags.

---

