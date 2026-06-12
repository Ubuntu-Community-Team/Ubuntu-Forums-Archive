---
title: "Headphones do not short speakers"
date: 2010-03-19
forum: Hardware
---

### Post by unueco on 2010-03-19
I have a very odd problem that I am assuming has something to do with how 9.10 is accessing and controlling my sound card.

I have a dual boot system between XP serv pack 2 and 9.10 Karmic.

*IF* I have muted the speaker when operating on the XP side, when I boot Ubuntu, I ONLY have sound coming from my headphone jack.

*IF* I unmute the speaker on the XP side, when I boot Ubuntu I ONLY have sound cming out of the speakers. Nothing comes out of the headphones and if I insert headphones into the jack, it does NOT short out the speakers.

*IF* I have muted the speakers on the XP side and am operating under condition 1 above, and then I make a call with Skype, it activates the speakers and puts me into condition 2 above. (Actually, this has only happened once just now...I haven't verified its consistency)

Advice/assitance appreciated!!

---

### Post by Fafler on 2010-03-19
I had a similar problem with my old laptop using intel-hda. Suddenly is started working as it should, probably after a update. Have you looked in Sound Preferences as to if you can turn volume up/down individually?

---

### Post by unueco on 2010-03-21
I think I have found at least a partial answer to this problem.

Right click on the speaker icon -> sound preferences -> output tab

Selecting "analog output" enables speakers (no headphones)
Selecting "analog headphones" enables headphones (no speaker).

So apparently 1) by design the headphones do not automatically short-out the speakers 2) for some reason, switching between the Win XP side and Linux side causes the default setting to change.

---

