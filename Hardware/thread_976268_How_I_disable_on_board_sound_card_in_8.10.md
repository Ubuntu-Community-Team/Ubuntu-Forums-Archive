---
title: "How I disable on board sound card in 8.10?"
date: 2008-11-09
forum: Hardware
---

### Post by rebelrex on 2008-11-09
hi!

I have 2 sound cards: sb live and onboard sound card.
For some reason the onboard sound card which is disabled in bios is detected in ubuntu 8.10, and that gives me problems.
I want to disable it, so ubuntu will think I only have 1 sound card - SB LIVE.

I read somewhere that in older versions what I needed to do is to blacklist the module of the sound card which I dont want to activate.
and that I do by going to :/etc/modprobe.d/blacklist
and adding line:
blacklist modulename

Is this also the way in 8.10?

---

