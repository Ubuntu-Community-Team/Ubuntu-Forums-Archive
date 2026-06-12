---
title: "Tascam US-122 problems"
date: 2011-12-14
forum: Hardware
---

### Post by JohnDillinger43 on 2011-12-14
I found several unanswered posts about getting a Tascam US-122 preamp to work with Ubuntu, so I thought I'd add one of my own :/  Like those who have posted before, I followed the instructions for installation that were kindly posted on this forum, and got the Tascam to be recognized and connected via USB.  It now shows up on the "input" list under Sound Settings.  However, it doesn't show up on the "output" list.  A more immediate issue is that I have the Tascam connected to my sound card via an A/V-->1/8" cable.  When I'm running WinXP, this allows me to monitor the output through my computer speakers, but for some reason when I'm running Ubuntu (11.10), I'm getting no sound.  The input in this case is a guitar hooked up to the line-in inputs on the Tascam -- the Tascam lights up when I'm playing, so the problem is between the Tascam and my sound card (X-Fi).  Hoping someone knows how to solve this issue.

---

### Post by JohnDillinger43 on 2011-12-16
Found the problem -- the line-in input on my sound card was muted.  I just had to go into alsamixer and unmute line-in.

---

