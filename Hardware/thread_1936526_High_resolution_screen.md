---
title: "High resolution screen"
date: 2012-03-06
forum: Hardware
---

### Post by dargaud on 2012-03-06
Hello all,
I'd like to get a high resolution screen beyond the usual 1920x1200 resolution, such as the [SyncMaster S27A850D]("http://www.amazon.com/exec/obidos/ASIN/B0050X2YZQ/guillaumedarg-20") which has a resolution of 2560x1440. Now I've heard that such resolution are not supported by standard graphic cards.

So the question is: how can I know if my graphic card can take it at its full resolution ? I have an ATI Radeon HD 3300 on my main PC and a nVidia Corporation GT218 [NVS 3100M] on my laptop.

Thanks.

---

### Post by lukeiamyourfather on 2012-03-06
Monitors like that typically require what they call dual-link DVI. If the video chipset is on the motherboard it probably won't work. Almost all modern discreet graphics cards support dual-link DVI.

---

### Post by dargaud on 2012-03-06
Can the dual-link capability of a graphic card be found with a command such as lspci or only by poring over the hardware specs ?

---

### Post by 1clue on 2012-03-06
[http://www.nvidia.com/object/nvs_techspecs.html](http://www.nvidia.com/object/nvs_techspecs.html)

---

### Post by dargaud on 2012-03-07
Err, thanks for the lmgtfy link. I did search first, using the specific reference to the cards, and did not find anything. That table lists resolution in VGA, HDMI and DisplayPort modes but not in DVI !

As for my main PC, I think I found the answer [here]("http://www.asrock.com/mb/overview.asp?Model=M3A790GXH/128M"): Supports Dual-link DVI with max. resolution up to 2560x1600

---

