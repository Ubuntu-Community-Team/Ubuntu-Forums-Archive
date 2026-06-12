---
title: "Turn off discrete AMD graphics card"
date: 2017-12-09
forum: Hardware
---

### Post by codedmart on 2017-12-09
This is a new install of Ubuntu 17.10

I want to turn off my discrete AMD graphics card. I have tried `radeon.modeset=0` which then `vgaswitcheroo` doesn't show under `/sys/kernel/debug/vgaswitcheroo/switch` anymore but I suspect it is still on as battery life still isn't at it's best. If I run `echo OFF > /sys/kernel/debug/vgaswitcheroo/switch` battery life is better, but if I run it while in X (Gnome) I start to get lockups. So I would like to try running `echo OFF > /sys/kernel/debug/vgaswitcheroo/switch` before X even starts. What is the best way to do that or does anyone have any other ideas on how I should completely power down my discrete AMD card?

---

