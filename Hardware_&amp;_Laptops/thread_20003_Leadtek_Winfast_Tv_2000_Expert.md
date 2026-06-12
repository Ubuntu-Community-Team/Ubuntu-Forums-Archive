---
title: "Leadtek Winfast Tv 2000 Expert"
date: 2005-03-14
forum: Hardware &amp; Laptops
---

### Post by nerozen on 2005-03-14
Hi

I'll like to see TV on my Ubuntu but i have a problem with my TV-CARD i have the image but i haven't the sound with zapping ( SECAM-L )

How can help me to make work properly my tv card ?

Thank by advance,

A lost French Newbie

PS : Sorry for my english !!!

---

### Post by Hurin on 2006-01-27
I have exactly the same problem :(

Solution?

Anyone??

Thanks...

---

### Post by X.Ray.Wa on 2006-01-28
I have a Winfast TV card and all I did to get sound was to turn on the **Line In:** volume and that solved the problem

---

### Post by tipping point on 2007-02-10
I have the Leadtek Winfast TV 2000XP (running Ubuntu 6.06 Dapper Drake) using TVTime software, I get "no signal" blue screen. Is there something I've overlooked or haven't done?
Cable signal is there to my Win comp (Matrox) After install there was no indication that new hardware was found but it is listed in System-Administration-Device Manager as Bt878 Video Capture and Bt878 Audio Capture.

---

### Post by beefbowel on 2007-11-12
i have this card and seriously no one on these forums know how to fix it or if they do know they are not  sharing :(

---

### Post by beefbowel on 2007-11-12
got it to work in tvtime.  mythtv still says "failed to open card".  

anyway high five!

i'm not sure what i did but to the best of my knowledge i did these things:

looked in   /lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88
to see if the drivers were there.

then, i typed in root terminal         
```
modprobe cx88xx
```

i put  in /etc/modules
```
cx88xx
```

then i unscrewed the coxial cable from my leadtek winfast 2000xp expert's FM jack and screwed it into the TV jack.  what a difference that made!  i now have tv.  

but i still am mythtv-less.  any help would be appreciated.

---

