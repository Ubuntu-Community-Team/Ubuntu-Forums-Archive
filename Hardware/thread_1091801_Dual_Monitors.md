---
title: "Dual Monitors"
date: 2009-03-09
forum: Hardware
---

### Post by Alchemi on 2009-03-09
Hello. I have one monitor hook up to my motherboard and another to a  nvidia geforce 6200 card, only the one on the card is reading. When I use the nvidia manger to detect the other monitor it does not. Is there a way to have two monitors hook up to one system? There is another port on my n-card, white port not vga  I forget the name, I have an adapter that came with it to connect it from vga to the white adapter,Is there way to hook that one up? I tried to plug it up but nothing comes on screen, so can I have two monitors on one box.

---

### Post by tweellt on 2009-03-09
The other port that you are talking about must be a DVI output (I think).

Anyway... What version of Ubuntu do you have?!

Are you using the Alsa Driver 177?!

I'm currently working with two monitors using my laptop without any problems.

Regards,
Tweellt.

---

### Post by tweellt on 2009-03-09
Wait a minute... I read your thread again... You said that you have one monitor connected to your Onbard Graphic and another one connected to the graphic board?!

If so, I don't think that would work.

If you have a NVidia with dual output you should be able to use it... The adapter that you were talking about (Dongle)  should do the work!

Like I said... only use the outputs from the NVidia Board, VGA and DVI with the adapter to VGA, and make sure that you have Alsa 177 Drivers. Then use System >> Administration >> NVidia X Server Settings.

Regards,
Tweellt.

---

### Post by JoeJJohnsonII on 2009-03-09
You might want to check your BIOS settings to make sure your on board video isn't disabled. Most motherboards will disable their on board video by default if it detects a video card installed.

---

