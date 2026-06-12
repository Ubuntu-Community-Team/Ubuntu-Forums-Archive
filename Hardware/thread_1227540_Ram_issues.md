---
title: "Ram issues"
date: 2009-07-30
forum: Hardware
---

### Post by 37fleetwood on 2009-07-30
Ok, I tried to get this figured out but there seems to be no good answer. I looked in the pdf for the mother board, searched the web etc. and nothing came up.
here's the situation. I thought I would upgrade my ram a bit. the mother board has 3 slots capable of 1 gig each. I had a 1 gig and a 500 meg running so I bought 2 1 gig sticks of ram. when they came I took out the 500 meg and installed the 2 1 gig sticks and the computer wouldn't start. I guessed that the 2 new sticks might need to be in the first 2 slots so I moved them. next the computer would post but crash just past the grub menu. next I took out the old 1 gig stick leaving the 2 new 1 gig sticks and it runs fine but this isn't what I wanted, I wanted 3 gig. my guess, and it's only a guess, is that since the new ram is dual channel it wanted to be in the first two slots and now the original 1 gig not being dual channel is now not compatible. does anyone now if this might the case. I also saw on the web that sometimes mother boards require dual channel to use slots 1 with slot 3 for dual channel. my board has only 3 slots so I'm wondering if I put the new sticks in 1 and 3 and the old one in 2 might it work? anyway if anyone has any ideas or information I would be very appreciative!
thanks
Scott:D

---

### Post by kerry_s on 2009-07-30
so what are we suppose to tell you?
you didn't provide any info about anything, motherboard, type of ram, link to that pdf?

so the basics, ram should always be matched, not a good idea to mix and match. 2gigs is still better than 1.5gigs :D

---

### Post by 37fleetwood on 2009-07-30
not that it matters too much but the original 1 gig is Kingston KVR333/1GR the 2 new sticks are generic dual channel ram from ebay. the mother board is a Jetway P4X400DB. my main issue is that the motherboard has 3 slots so it can't expect dual channel with 3 slots can it?
new information, I shut down and moved the odd stick to slot 2 and it booted through grub to the login screen but after typing name and pass it crashed. Windows also booted most of the way but crashed. on a whim I installed the 500 gig stick and it works perfectly, so the issue is apparently in the 1 gig Kingston stick. it is somehow incompatible.
I guess the answer I was looking for was, if you are running a matched pair of dual channel ram can you then add a single stick of non dual channel ram? apparently the answer is no.

---

### Post by dlmarti on 2009-07-30
> **37fleetwood said:**
> not that it matters too much but the original 1 gig is Kingston KVR333/1GR the 2 new sticks are generic dual channel ram from ebay. the mother board is a Jetway P4X400DB. my main issue is that the motherboard has 3 slots so it can't expect dual channel with 3 slots can it?
new information, I shut down and moved the odd stick to slot 2 and it booted through grub to the login screen but after typing name and pass it crashed. Windows also booted most of the way but crashed. on a whim I installed the 500 gig stick and it works perfectly, so the issue is apparently in the 1 gig Kingston stick. it is somehow incompatible.
I guess the answer I was looking for was, if you are running a matched pair of dual channel ram can you then add a single stick of non dual channel ram? apparently the answer is no.

you purchased the wrong ram from ebay.

---

### Post by kerry_s on 2009-07-30
according to google that board can take 3gigs of 184pin pc2700, you can also use pc2100 or pc3200, but there just compatible.

so what did you get from ebay?

---

### Post by 37fleetwood on 2009-07-30
> **kerry_s said:**
> according to google that board can take 3gigs of 184pin pc2700, you can also use pc2100 or pc3200, but there just compatible.

so what did you get from ebay?
here's what I got:

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=180376404297&ssPageName=STRK:MEWNX:IT](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=180376404297&ssPageName=STRK:MEWNX:IT)
there aren't a lot of choices for older ram. my main concern was to make sure I got low density ram. I could always just get 1 more stick from this seller and it should work.

---

### Post by 37fleetwood on 2009-08-06
well I figured it out. After trying everything I could think of, I took them out and sat there looking them over and was amazed to find this:
[IMG]http://i14.photobucket.com/albums/a315/hotshot66/puppy/img_1417.jpg[/IMG]

why there is solder on the contacts I'll never know. the ebay seller has offered to simply replace the bad one no questions asked. for now I'm running the old 1gig the 500meg and the other new 1gig with no problems. 2.5gig of ram til the replacement comes, not bad.

---

### Post by dlmarti on 2009-08-06
sweet, nice catch

---

