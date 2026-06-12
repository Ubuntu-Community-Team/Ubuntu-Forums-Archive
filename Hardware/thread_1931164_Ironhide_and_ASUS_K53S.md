---
title: "Ironhide and ASUS K53S"
date: 2012-02-24
forum: Hardware
---

### Post by cj_g0bl1n on 2012-02-24
I recently bought an ASUS K53S, great laptop, however it comes with Nvidia's Optimus.  I had no idea it was going to interfere with the graphics card (I only bought it because it had a 2GB Nvidia 610M and I do a lot of computer graphics programming on Linux).  So I've done a bunch of research, been through almost every tutorial on the net, and I finally came to Ironhide as a solution.

Sadly I installed it (without errors) and my graphics card isn't performing at the efficiency it should be (on glxgears I get around 60 FPS, from what I understand this should run at around 3000 to 4000 FPS, and yes I know glxgears isn't a benchmark, but when I get much higher FPS on a 128 MB ATI card I'm a little concearned).  I'm debating returning the laptop (although I REALLY like it, size is perfect and the price was very low).

I'm hoping someone can help me before I have to let this beauty go.  I have two questions:

Is there a way to make sure the video card is performing correctly and I'm not just paranoid that glxgears should be running faster?

If so what can I try to fix this?  I'm not sure if I have to right ACPI commands, I couldn't find the ones for my laptop specifically, but it seems like the K52J series has a very similar design, so it hopefully uses the same commands, I could be wrong...

Thanks for any insight into my current dilemma,
Goblin

EDIT:
Ahh, I tried to run a game and viola:
DON Enabling nVidia card failed (Error: AE_NOT_FOUND).

So it isn't running on the Nvidia card, and thats why the power performance difference...

---

