---
title: "Belkin N52te... does not play well with Pystromo"
date: 2011-01-02
forum: Hardware
---

### Post by ShneekeyTheLost on 2011-01-02
Okay, I'm a fairly new user to Ubuntu 10.10, and I really prefer it over anything windows has out, but I've got one slight issue...

I've got a Belkin N52te. It's not an N52, for which Pystromo is an excellent way to get it to work. Let me try and explain why precisely it won't work well, and then we'll see if there's anything to see if I can fix the problem.

First off, the 'te' at the end stands for Tournament Edition. It was originally created with the idea that a 'pro gamer' could take this, plug it in anywhere, and be able to run all his macros and hotkeys for an enhanced gaming experience. Of course, no real tournament would let you bring in your own hardware, so the idea itself was flawed, but because of this concept, there's a very major difference in firmware.

Y'see, the old N52 runs like most hardware... you run the driver, it activates the device, and interprets, yadda yadda.

The N52te, on the other hand, saves a profile 'on board', which it automatically uses. The driver isn't needed to run the device, it's just needed to change the settings. 

Right now, I can plug the thing in, no drivers, and the buttons will be active with whatever the last profile I uploaded to it was. What I cannot do, however, is change which profile to use.

I tried to use Pystromo, even figured out what the numbers were for the thing so it could 'grab' it when it was plugged in. But pystromo doesn't seem to be a very good resource for the n52te because unlike the 50/52, it does not use a driver to interpret button presses, but instead stores them onboard. This also hopelessly scrambles the method which Pystromo uses to change configurations, as the buttons could currently be defined as just about anything, depending on what the last profile uploaded to it was.

What I need is a small daemon which will allow the n52te to be recognized as being attached to the computer so I can then run the editor in WINE to change profiles. Is there anything that can do this?

---

