---
title: "Touchpad Recognized but not Firing Events"
date: 2016-05-09
forum: Hardware
---

### Post by Gabriel_Smith on 2016-05-09
So I have a Toshiba Satellite U845W that used to run Ubuntu marvelously, or at least well enough for me not to complain. At any rate, I also require Windows for a few pieces of software so I have everything set up in a dual boot setup. No issues there as I'm not new to this roadshow. I think the problems started when I ran Speedfan one time, it locked up, I had to force the computer to restart, and one of the two (yeah, two) Synaptic touchpads recognized by Windows disappeared without a trace. The touchpad that disappeared was a version 2.2 if I remember correctly, and the other remaining one is a version 1.2. At any rate, everything continued to work in Windows, though I did have to set my mouse settings for the Synaptic features all up again. I later booted into Ubuntu and found that the touchpad refused to work. Xinput and the input devices both list the Synaptic touchpad but evtest shows no events being created. I have tried mucking about in Windows to get the other device to show up again with no luck. I will leave both the evtest report from me clicking and dragging on the touchpad as well as my Xorg.0.log file attached. I had to compress the Xorg.0.log file to make it fit on the forums. Any help?

[ATTACH]268968[/ATTACH]
[ATTACH]268969[/ATTACH]

---

