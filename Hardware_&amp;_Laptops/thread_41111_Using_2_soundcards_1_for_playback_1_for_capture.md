---
title: "Using 2 soundcards 1 for playback 1 for capture"
date: 2005-06-11
forum: Hardware &amp; Laptops
---

### Post by veda_sticks on 2005-06-11
I bought a sound blaster live 24 bit 7.1 card by mistake and after getting the right drivers for it, realise that it only supports playback.
What id like to do is use my sb live for sound playback and my onboard (abit an7 motherboard) for recording if this is possible. If not then if there is a way to switch between the devices that would be great, I really need capture support as i use team speak for meetings with people across the internet and i need to be able to record from my minidisk onto pc for processing and finalize to CD. Live sound and stuff. 
If anyone knows of a way to do this, great :)

---

### Post by felipe on 2005-06-12
why don't you simply remove the half-working card?

using two or more cards contemporarily is possible, but you'll probably get phasing problems due to synchronization.

check the alsa documentation on how to create a proper .asoundrc file to accomplish that, be warned: it's not trivial :/

---

