---
title: "Touchpad too slow"
date: 2007-06-07
forum: Hardware &amp; Laptops
---

### Post by jimbren on 2007-06-07
I'm looking to improve the speed of my mouse pointer for my Dell D400 laptop.  I'm using a Symantics Touchpad that seems to be properly configured, but the mouse is still painfully slow and always has been, regardless of what version of Ubuntu I'm using.  (currently Kubuntu 7.04)

Anyway, my xorg.conf looks like this: 
```
Section "InputDevice"
  Identifier "Synaptics Touchpad"
  Driver "synaptics"
  option "SendCoreEvents" "true"
  option "Device" "/dev/psaux"
  option "Protocol" "auto-dev"
  option "HorizScrollDelta" "0"
EndSection

```

What does the HorizScrollDelta control?  And will I see an improvement if I change the value?

Thanks,

jimbo

---

### Post by jimbren on 2007-06-08
Some more digging would have answered my own question, had I not been lazy about it.  I installed ksynaptics, and now I'm able to more fully configure my touchpad's responsiveness.  

Kubuntu users would install ksynaptics, and Ubuntu qsynaptics.

Your mileage may vary.

jimbo

---

### Post by jimbren on 2007-06-09
After playing with ksynaptics for a day, I decided it was a step backwards and removed it.  The touchpad became very sensitive and tended to wander, and tapping stopped working.  It also didn't provided much of an improvement in the pointer movement speed, which is what I was looking for inthe first place.  

Back on the hunt.

ideas?


jimbo

---

### Post by anthonyp on 2007-06-17
I too am on the hunt to a solution although i am very new to ubuntu and need to be hand fed the info :D

---

### Post by HotShotDJ on 2007-06-17
Have you tried (in KDE) System Settings --> Keyboard & Mouse --> Mouse, click on the "Advanced" tab and use the slider to increase pointer acceleration?  Worked for me.  (In kcontrol, it is found under Peripherals --> Mouse, Advanced tab)

And I agree that KSynaptic is horrible.  It made things worse for me rather than better.

---

### Post by KillerSiafu on 2007-11-10
Not sure if you've solved this problem yet or not, but my touchpad on my inspiron 1420 was moving extremely slow (running gutsy). I added the following lines to my xorg.conf under the Synpatic Touchpad section. Of course you can tweak these settings to your liking.

        Option "MinSpeed" "0.60"
        Option "MaxSpeed" "1.10"
        Option "AccelFactor" "0.030"
        Option "EdgeMotionMinSpeed" "200"
        Option "EdgeMotionMaxSpeed" "200"
        Option "UpDownScrolling" "1"

Hope this is helpful

---

