---
title: "how can I verify if no sound bug is from hardware or lack of a driver?"
date: 2013-09-22
forum: Hardware
---

### Post by HamHamT on 2013-09-22
i have a zenbook UX31E and I just started to realize that I am getting no sound out of the left speaker.  i checked in the sound settings and when I put the sound balance all to the left I get 0 sound from my unit.  I just sent my zenbook back to asus to fix a random shutdown bug i had, and when it returned i just took note of this.

my sound card, i believe is:

```
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)

```

how can I go about upgrading the driver (or kernel of this device if i am understanding the use of this term) to see if that will fix the problem or should I contact asus again?

thank you!

---

### Post by tgalati4 on 2013-09-22
Sounds like they either:

1.  Forgot to plug in the left speaker.
2.  Broke or pinched a wire when reassembling.  It happens.

If you go to Sound Preferences and select the "Hardware" tab you will see a button labeled "Test".  You will hear a voice:  "This is the Left Speaker; This is the Right Speaker."

Looks like you might have to return it.

---

### Post by HamHamT on 2013-09-22
thank you

---

### Post by tgalati4 on 2013-09-22
If the sound is working with headphones in both ears, but you only hear the right speaker when the headphone is unplugged, then you can be reasonably sure that the left speaker is inoperative.

If both the left headphone and left speaker are not working, then it might be a soundchip problem. Intel sound chips are generic and generally work without fuss.

Out of curiosity, what was causing the random shutdowns?  A defective motherboard?

---

### Post by HamHamT on 2013-09-23
> If you go to Sound Preferences and select the "Hardware" tab you will see a button labeled "Test". You will hear a voice: "This is the Left Speaker; This is the Right Speaker."
only returns the dialouge from the right speaker, so I need to call asus again it seems.

the random shutdowns according the asus had to do something with AC port where you plug in the charger being faulty. i orginally thought it might have been a problem from installing Linux (i had windows 7 installed stock on my computer for about 15 minutes before I decided to hack it :) ) but after updating the bios I still had the same problem.

---

