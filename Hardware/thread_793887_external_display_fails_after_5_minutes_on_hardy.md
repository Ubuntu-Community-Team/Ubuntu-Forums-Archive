---
title: "external display fails after 5 minutes on hardy"
date: 2008-05-14
forum: Hardware
---

### Post by carloscuev on 2008-05-14
I need help, when i had ubuntu gutsy i had no problem using a external monitor with xrandr, but now that I'm on hardy the external display fails (its still with backlight ON) and the screen goes all black and theres no other way than rebooting to have approximately another 5 - 10 minutes of image on the external display. The external display I use is a Benq FP91G+.

I have an Intel 945GM card, the laptop is a Toshiba Satellite A205-S4607

I have searched two days for a fix and I haven't found nothing more than:

1. The problem may be a wrong auto detection of the frequencies of the external display, also I've searched the correct frequencies for my display and they are: H: 31 KHz - 83 KHz, V: 56Hz - 76 Hz. Is there a way to force this values in the xorg.conf? if so, is there also a way that only with this display it uses this frequencies? because at school sometimes I use a projector for my presentations.

2. Ubuntu Hardy uses some new version of xserver that autodetects everything, even the "dpkg-reconfigure xserver-xorg" command doesnt asks you about any graphics, it now only asks you about the mouse and keyboard.

Some hours ago, the update manager showed up a intel driver update "xserver-xorg-video-intel" and I thought it would be the solution, after installing and rebooting the problem was still there.

Any information would be greatly appreciated, thanks.

---

