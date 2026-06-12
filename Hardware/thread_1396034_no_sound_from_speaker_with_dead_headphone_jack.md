---
title: "no sound from speaker with dead headphone jack"
date: 2010-02-01
forum: Hardware
---

### Post by elcoincoin on 2010-02-01
Hi everybody!
I've got a little problem on my Dell Studio XPS 16.
Actually, i damaged one of the 2 headphone jack on the laptop. So, for instance, on Windows Vista, the audio software thinks that there is always a headphone plugged.
Consequently, in both Vista and Ubuntu (last version), I've got not sound from speakers, but only from earplugs.

Actually, speakers are not dead: there is an hardware test on the Dell, and it succeed in broadcasting some music on the speakers. (so there is not only an hardware switch between headset and speakers, it could be made through software).

Do you think there's could be a solution to my problem? Could you provide me some help?
(I've already try to manage it through alsamixer with no success).

Thx a lot!

Elcoincoin

---

### Post by elcoincoin on 2010-02-02
up

---

### Post by elcoincoin on 2010-02-03
up

---

### Post by Zorael on 2010-02-03
Basically, you want to force the soundcard to ignore its headphone jack detection and output through speakers anyway? Hmm.

As you said, it's definitely possible through software, but unless you have a Headphone Jack Detection switch in alsamixer, the driver probably just doesn't offer that functionality. Perhaps it's all governed by hardware unless you have the exclusive access only the makers of it are privy to.

Your options;
[list][*]Spoof your soundcard as of a different model, causing the driver to fail at jack detection. This is at least possible with soundcards using the **snd-hda-intel** module. (**lsmod | grep snd-hda-intel**) (barring hardware limitations)
[*]Download the driver source, find the part relevant to your soundcard model, comment out whatever manages jack detection and compile
[*]Fix/replace the hardware :3[/list]

---

### Post by elcoincoin on 2010-02-05
Hey thanks Zorael for your answer! :D

[LIST]
[*]The module (**snd-hda-intel)** is used by my laptop. Consequently i will try to change the model of the driver (but there are tons of models... which one should I try???).
[*]Where can I find the driver source of my sound card? I guess it will be hard for me to find the part to comment, but, why not trying.
[/LIST]

---

