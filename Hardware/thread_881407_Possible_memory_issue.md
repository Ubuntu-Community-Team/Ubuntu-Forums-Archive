---
title: "Possible memory issue?"
date: 2008-08-06
forum: Hardware
---

### Post by jmerkin on 2008-08-06
I've a couple year old laptop and after deciding that I'm going to wait a year until replacing it, I maxed the RAM out on it (should have done it earlier but oh well). Since then I have been having memory issues, where firefox would crash while playing a flash video and similar things. At time, it would freeze the system to the point where I can't switch to a virtual terminal or log out and I would have to reboot. When I reboot, I can't open firefox because it says something about it being open, though pidof shows no firefox.

So I'm thinking I got some bad RAM. Is this a good guess, or could it be something else? The issue may not have occurred at the same exact time, just around the same time. How can I test for it in ubuntu? I haven't adjusted the swap partition yet to accommodate the increased RAM (went from 512mb to 2gb) because I am waiting until after I attempt to replace the power jack on the mobo (common problem for these apparently, had to figure it out after warranty and HP support sucks), as it's too costly to pay someone to do it on such an old laptop when a new one can be had for not much more.

In short, could this be bad RAM, or something else, and how can I test for that?

Thanks. And if it makes a difference, I'm running kubuntu hardy.

---

### Post by tamoneya on 2008-08-06
sounds like bad ram to me.  You should use memtest.  It is included on the ultimate boot CD.  Just burn it like you do with a normal ISO and then boot from the disc.

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

---

### Post by jmerkin on 2008-08-06
Thanks for the suggestion. I used memtest86+ and let it run overnight. It went through 4 passes and found no errors. Should I run another test?

It's been unreasonably glitchy lately so I may just try reinstalling.

---

### Post by tamoneya on 2008-08-06
I was betting on bad memory but I guess not. If it had 4 successful passes that is pretty reliable.  I guess a reinstall cant hurt but im not certain exactly what it will fix.  Are the memory sticks operating at the same speed?

---

### Post by jmerkin on 2008-08-06
Yeah. I bought them together off Newegg the other day. Old laptop, so they are DDR1The most noticeable other glitch is it randomly logging me out, but that only has been happening for hte past couple days, so I don't know. Any ideas? I'll probably be reinstalling kubuntu or trying my hand at debian tonight, so I'll see how that goes.

---

### Post by evets25 on 2008-08-06
It does sound like memory-related issues, but OTOH, the issue with firefox and flash is probably just an issue with firefox and flash (not something more sinister), which is not surprising. If it is memory/hardare related, then you should notice other weird random problems with other programs and with your system in general. If it's just firefox, then it's probably just a software problem with firefox, and completely unrelated to your ram issue.

---

