---
title: "Heat prob with 4780x2"
date: 2008-12-15
forum: Hardware
---

### Post by logiq on 2008-12-15
Hello everyone.

I was wondering if it is possible to set the fan speed on my graphic card in Ubuntu?

I have an ATI 4780x2 card, that does 80c when idling, and the PC crashes frequently.

I started the terminal and tried something like this:
```

sudo aticonfig --pplib-cmd "set fanspeed 0 50"
```

(Which I got from another forum..)

But I receive this error message:

```
PPLIB command execution has failed!
ati_pplib_cmd: execute "set" failed"
```

I am a total newbie at Ubuntu, started today, so its possibly that I am doing something wrong.

When I ran vista, I just used the catalyst driver tweak to increase the fan speed, but It doesnt seem that the ATI-Linux driver has this feature (Which it really should have! Many has the same problem)

After googling for about 2-3 hours I decided to post here.

Any suggestion would be appreciated allot!

Cheers.

---

### Post by elvinatom on 2008-12-15
open the case and look at the airflow (is the video card between intake and exhaust), add fans, make sure video card fan works.

---

### Post by logiq on 2008-12-15
I can bearly fit more fans in my case. But heat problem with the 4780x2 is a well-known problem, which got a work-around in windows. So I just wondered if anyone had came up with a solution to Linux. i.e, control the fan speeds.

---

### Post by elvinatom on 2008-12-15
Well, sorry to tell you, but ATI support for Linux kinda sucks.  The drivers lack quality and quantity.  I used to love my ATI cards but I had to say 'goodbye!' when I came to Linux.

---

