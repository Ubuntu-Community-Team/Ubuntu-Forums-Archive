---
title: "LG HBM-760 bluetooth Headset will not work &gt;.&lt;"
date: 2009-11-19
forum: Hardware
---

### Post by powerplayground on 2009-11-19
Alright I've followed a bunch of guides (all different) on how to get my bluetooth headset working. None of them worked. I added this to my ~/.asoundrc file:

> pcm.btheadset {
type bluetooth
device 00:05:C9:BB:10:A7
profile "headset"
}

It recognizes fine in blueman, but there is no way to set it to be the default input/output for sound. And when I click setup in blueman, the page is blank.

Also fail on Ubuntu for not streamlining this process. Every other OS and Device in the world has made pairing Bluetooth devices the easiest thing on the planet, but I still have to do everything manually on Ubuntu? F-F-F-Fail!

---

