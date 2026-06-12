---
title: "X-Fi Audio Corruption"
date: 2011-04-19
forum: Hardware
---

### Post by spodesabode on 2011-04-19
Hi Guys,

I'm running 10.10 64-bit on an Intel DX48BT2 motherboard. I've got an X-Fi Xtreme Something (Music I think). lspci says:

03:00.0 Multimedia audio controller: Creative Labs SB X-Fi

It works fine - but during boot when pulseaudio initializes I hear a high pitched noise for a split second.

Then periodically, say during a Skype call, the sound will become all quantized and be repeating like it's on some sort of feedback loop.

If I then issue a pulseaudio -k it solves the problem for a couple of minutes before coming back.

This isn't a Skype issue - it's happening in other apps too.

I'm not sure how I would go about solving this?

---

### Post by goatboy73 on 2011-05-15
BUMP!

I'm having this issue too - fresh install of Natty 32-bit, with an X-Fi Titanium series.

This was happening before with Maverick as well. It's VERY unpredictible, but killing pulse and re-starting it fixes it - sometimes for a few minutes, sometimes "permanently".

The audio I hear is a "raspy" (or corrupted) version of the actual correct audio, but I hear it twice (both times corrupted in similar fashion).  The second time comes a fraction of a second after the original - 200ms at least, possibly as much as 500ms or even 1s (haven't tried to time it).

Anyone have any ideas on how we can provide further information to help debug this?

---

