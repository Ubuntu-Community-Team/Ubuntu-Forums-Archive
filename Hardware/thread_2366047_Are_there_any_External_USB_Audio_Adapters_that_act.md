---
title: "Are there any External USB Audio Adapters that actually work with Linux/Ubuntu?"
date: 2017-07-13
forum: Hardware
---

### Post by toxicious on 2017-07-13
I just bought my third external audio adapter for use with my laptop. Sadly, I also just discovered that it doesn't work, just like the other 2.

Yes I get sound. Yes it sounds alright. And yes, there are several major problems with all of them:
[LIST]
[*]Muted when sound is below x% (usually 20-30%) (I know there is a fix for this by editing an alsa file, but that fix seems to affect all audio cards, which is dumb)
[*]Noise in certain scenarios
[*]Microphone is extremely low
[/LIST]

Two of them are the typical china stuff you find cheap online.  The latest one I got is an ASUS Xonar U3. Outdated but still performs well on Windows.
The annoying part here is clearly that all of these work fine in Windows 7/8/10 etc.

I do not wanna know how many hours I have spent trying to figure out how to get these things working either. 99% of the advice you find online is to use alsamixer or pavucontrol, which I have of course tried without success. Every time.

So, my question is, is there even an external audio adapter (USB) that works with Ubuntu/Linux? Clearly, there is not difference between an adapter for 10 bucks (C-Media) and one for 50 (U3). Do you have to go higher? $100? $200?

It is also worth noting that I have tried these on two completely different (brands, types) laptops as well. Also, the on-board sound works great on both of these laptops, I just want extra outputs/a "dockable" laptop (one or two USB instead of 5 different chords going into the laptop).

---

### Post by toxicious on 2017-07-17
I'll take that as a no.

---

### Post by termibuntu on 2017-07-17
There are, but they have to actually SUPPORT Linux. Some work with Linux out of the box, some need extra setup and some won't. Also, please don't be raging. We are here to help.

---

### Post by oldos2er on 2017-07-17
Hmmm, no raging that I can see, just some understandable frustration plus a valid question.

@toxicious The Hardware subforum might be a better fit for your question. If you'd like me (or any member of staff) to move it there, just say the word.

---

### Post by toxicious on 2017-07-19
> **oldos2er said:**
> Hmmm, no raging that I can see, just some understandable frustration plus a valid question.

@toxicious The Hardware subforum might be a better fit for your question. If you'd like me (or any member of staff) to move it there, just say the word.

Thanks for understanding. I was just surprised that there wasn't any known brands or models that were listed as working OOB. However, yesterday I magically found the fix to the volume issues. The solution is the pulseaudio ignore_db flag. With that one on, suddenly all the external audio adapters' volumes now work as intended. Crazy :guitar:.Took me 2 years to find this! I am surprised it is not more well-documented/known. Furthermore, I am surprised it is not on by default for external adapters.

Nonetheless, if you feel like moving this thread to hardware could help more people (I think it potentially could), then please go ahead and do so.

---

### Post by HermanAB on 2017-07-19
Well, there is no correlation between quality and price.

I have had no issues with Logitec sound devices, so maybe try something from them.

---

### Post by oldos2er on 2017-07-19
Thread moved to Hardware.

---

