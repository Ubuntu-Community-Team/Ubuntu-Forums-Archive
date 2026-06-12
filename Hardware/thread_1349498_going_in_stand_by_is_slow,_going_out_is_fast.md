---
title: "going in stand by is slow, going out is fast?"
date: 2009-12-08
forum: Hardware
---

### Post by P3t3r on 2009-12-08
Standby is going really slow on my Toshiba Portege R600 laptop. At least going into standby mode. Going out of it takes less than a second. Which is strange.

Going into standby takes pretty long, I guess a minute or so, while there is basicly nothing to it. It almost looks like it waits for something to time out. But I have no idea what: the screen goes black (but with backlight on) and then it takes a minute before the fan stops and the light goes out).

Can anyone guide me how to resolve this or how to find the culprit? 

Might be a relevant detail: I'm not using swap space (I have 3GiB memory).

---

### Post by P3t3r on 2009-12-18
Anyone? Is there a way I can see what happens while going into standby (which may help identifying the problem)?

I measured the time of suspend to ram (=standby): 
 - suspend: 2 minutes 9 seconds
 - resume: 8 seconds

so I presume something takes 2 minutes to time out...

(Suspending to RAM takes as long as a cold boot --> that is not normal.)

---

### Post by P3t3r on 2009-12-29
No answer for two weeks... :(

I can't find anything useful in dmesg, are there any other things I can try?

---

