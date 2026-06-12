---
title: "Aureon Sky Soundcard issues"
date: 2005-11-24
forum: General Help
---

### Post by Kræn Knude on 2005-11-24
Hi there, I'm quite new to ubuntu (and linux generally) and I have tried to get my sound card working the last couple of days.

The problem is:

I have 2 sound cards installed. I have a normal ac97 soundcard integrated in the motherboard (nvidia2 chipset), and besides that I have a Auroen Sky sound card in a pci slot.

- I can use the integrated ac97 card without problems.

- The computer recognize my Aureon card without problems, but i can't get any sounds out of it.

Here's what I've done myself to solve the problem (the card should be supported by alsa):

- I've made sure that all alsa components neccesary are installed. The alsa-mixer recognize the aureon too, but only when i write alsa-mixer -c 1.

- I've changed the default soundcard to aureon in the 'sound' setup in preferences. The weird thing is that the ac97 continues to work even though i do this.

- I've made sure that the sound card isn't muted anywhere.

What can I do to fix this?

My theory is that even though i've tried to make the aureon the default sound card, the ac97 still is, but i don't know how to change that manually.

---

### Post by Kræn Knude on 2005-11-24
Well, problem fixed...

I disabled my onboard soundcard in the bios, and the solved it. Yay! :D

---

