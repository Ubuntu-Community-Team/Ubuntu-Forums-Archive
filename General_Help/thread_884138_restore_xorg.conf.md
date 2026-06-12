---
title: "restore xorg.conf"
date: 2008-08-08
forum: General Help
---

### Post by chaosdesigner on 2008-08-08
Hello Users,

I have a little problem with my mouse. I have a Razer DeathAdder Mouse, if this is at all improtant. So right I read that to compleatly get the drivers fpr this mouse, I'd have to change the xorg.conf. It told me to copy/paste the following:

Section "InputDevice"
Driver "mouse"
Identifier "Mouse[0]"
Option "Buttons" "7"
Option "Device" "/dev/input/mice"
Option "Vendor" "Razer"
Option "Name" "Diamondback 1600c"
Option "Protocol" "ExplorerPS/2"
Option "ZAxisMapping" "6 7"
Option "Resolution" "1600"
Option "SampleRate" "2000"
EndSection

So i copied this over the old settings and saved it -> mistake. Now my mouse works worse than befor, because now my scroll-wheel doesnt work. Well now I just need to recover my old xorg.conf settings, but how?

thx

---

### Post by InfinityCircuit on 2008-08-08
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will restore your xorg.conf to the original.

---

### Post by tjwoosta on 2008-08-08
well i suppose you could try running the live cd and maybe copy the xorg.conf from that


oops, i guess i was too late, infinity's answer is better

---

### Post by chaosdesigner on 2008-08-08
Thank you, that worked.

Edit:

Didnt work so well after all, now I cant log on to Ubuntu anymore, only with the Terminal Session... What can I do? Could this be the problem?

---

