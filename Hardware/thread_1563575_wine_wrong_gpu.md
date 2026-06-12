---
title: "wine wrong gpu"
date: 2010-08-29
forum: Hardware
---

### Post by tadaskr on 2010-08-29
Hello,
Today I installed Colin Mcrae rally 2005 on my laptop using wine 1.3.1. and I have problem: when you go to options, graphics, advanced options and dispay adapter showing ATI Mobility radeon HD 2350, but my GPU is ATI mobility radeon HD 3470. I tried a lot games and same isue. In wine 1.2 is same. ATI catalyst control panel showing ATI Mobility Radeon HD 3400 Series. cmr 2005 isn't going smooth there is a lot frames drop. So there is wine problem or my ATI drivers?

---

### Post by Fafler on 2010-08-29
First, it's normal for Wine to "fake" another graphics adapter than you actually have. I've seen it before and usually it doesn't cause problems. Most games doesn't really care if it runs on one model or another, but makes the software layer below, that being DirectX or OpenGL, care about it.

Second, if you're unsure whether your graphics driver works as it should, try running a native Linux game instead, to rule Wine out of the equation. I use Doom 3 for that. I think a demo can be downloaded from Id softs website.

---

