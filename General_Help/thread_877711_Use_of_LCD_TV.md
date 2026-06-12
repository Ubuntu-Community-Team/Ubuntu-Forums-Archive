---
title: "Use of LCD TV"
date: 2008-08-02
forum: General Help
---

### Post by Paul-G on 2008-08-02
I am using Hardy on a AMD dual core system with a Nvidia 7600 GT graphics card. I have just acquired a Sony KDL-26U2000 LCD TV which I wish to use as a monitor. So far I have tried using a DVI to HDMI cable, with the Monitor set to a LCD Panel 1360x768 and a screen res of 1280x720 and 1280x768. Both work but all the edges of the desktop are clipped. I have tried to use xvidtune to reduce the overall size, but all I get is error messages saying it is not possible to make changes. I have also tried an analogue  video cable, but the TV fails to display anything other than an out of range message.

Any one got any ideas.

---

### Post by coffeecat on 2008-08-02
I think you'll find that the LCD TV has a native resolution of 1366x768, but that the nearest resolution that the xserver can put out (with the appropriate graphics card driver) is 1360x768. Which I thought a bit odd when I experimented linking up my LG 32" LCD TV first to a Windows/Linux multibooting PC with Nvidia graphics card, and then with my MacMini. Actually, come to think of it, this discrepancy between the two resolutions wasn't limited to Linux - it was there with the Macintosh. I can't remember whether I bothered with Windows.

Anyway, when I connected up through the VGA ports, with 1360x768 selected on the computer, the image was poor - font-rendering distorted left to right. But I managed to find an 'autotune' facility somewhere in the TV menu - the equivalent to the 'auto' button you find on some/most LCD monitors. When I ran this, the image improved enormously with vertical strips of three blank pixels down the left and right edges. This was true with both Linux and the Mac.

With VGA, which screen resolution are you selecting in the GUI? If it's 1280x7** it's possible the xserver is putting out a refresh rate higher than the LCD can cope with. Try 1360x768 and see if you can find an 'auto' function somewhere in the TV menu.

I didn't bother trying to connect with a digital cable so, sorry, can't help you there, except - have you explored the further reaches of the TV menu? The options available sometimes change depending on the input source. There might be something there to deal with the clipping of the desktop.

---

### Post by sandyd on 2012-11-03
**Necromancing - thread closed**

A per the Ubuntu Forums Code of conduct, please do not post in threads more than one year old, as fixes and issues differ for each version of Ubuntu

---

