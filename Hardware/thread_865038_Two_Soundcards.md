---
title: "Two Soundcards"
date: 2008-07-20
forum: Hardware
---

### Post by icarusfall on 2008-07-20
Hello! I have a question that I think is quite basic, but I'm not sure.

Basically it's a new install of Ubuntu Studio (64 bit). I have two soundcards on the machine, one of them is the standard on-board sound, and the other is a more advanced one (it's an M-Audio Audiophile 2496). What I'm currently doing is using the on-board card for sound OUTPUT (connected via SPDIF, which seems to be working OK after unmuting it in alsamixer), but I'd like to use the other soundcard for INPUT (plugging a microphone via a pre-amp into the soundcard's RCA inputs).

So...sound output seems to be working OK, and aplay -l shows both soundcards. But I'm not sure if alsamixer is allowing both of them to work at the same time, is there an easy way to check whether this is possible? I've tried running soundrecorder and trying to test if the mike is working on each of the available capture channels that soundrecorder lists, but so far I haven't managed to get anything to record.

So my first question is "does Ubuntu allow you to use two soundcards simultaneously?", and if the answer is yes, then how can I use alsamixer to check if the channels are open for capture, because at the moment alsamixer only seems to have channels for the one soundcard.

I'm not sure if that's clear enough. If not, I'm sorry about that. I don't know if my setup is a very odd one, I would have thought it was quite common, but I wasn't able to find anybody with a similar problem.

Thanks

---

### Post by A. J. Rimmer on 2008-07-20
"does Ubuntu allow you to use two soundcards simultaneously?"

Hmmm ... I think so.  I have used my internal (motherboard) sound card and an external (USB) sound card at the same time, I think.  You can look at the settings for the various sound devices by typing (in a terminal window) "alsamixer -c0" for the first card and "alsamixer -c1" for the second card.  That will let you inspect and adjust the individual settings.

---

### Post by icarusfall on 2008-07-20
Brilliant. Thanks very much. The computer now can receive input from the mike.

My next question isn't really Ubuntu specific, so I don't mind if no-one's able to answer. I'm using Ardour to record the input, but it appears that Jack can only monitor one soundcard, with the result that although I can now capture sound, I can't play it back in Ardour.

I probably ought to just get a digital coaxial cable, and let the new card do both the input and output, I suppose.

---

### Post by icarusfall on 2008-07-21
Hmm, a bit of Googling tells me that Jack only really supports one soundcard, and that getting it to use two involves a fair bit of kludging around. I'll just buy that coaxial cable to connect my new soundcard to my speakers, I think.

---

