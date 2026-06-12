---
title: "Radeon Mobility 9200 vs. Intel X3100 vs. Nvidia 7150M"
date: 2008-08-13
forum: Hardware
---

### Post by Perpetual on 2008-08-13
I am looking at upgrading to a new laptop.  I currently have a Dell D600 with a Radeon Mobility 9200 graphics card.  This card works ok except I can not use an external monitor, it only clones the laptop screeen rather than upping the resolution to match the larger external monitor.

Question is, I am torn between 2 different HP's:

DV6910US w/ Nvidia Geforce Go 7150M 1071 mb's shared video memory

or...

DV6928US w/ Intel X3100 358 mb's shared video memory.

Will either or both support using an external monitor with the proper resolution?  Any other thoughts about the graphics cards?  I am not a gamer so intensive graphics are not a concern.  Mainly just the external monitor issue.

Thank you!

Landon

---

### Post by evets25 on 2008-08-13
asyncronous display (using two different displays with two different resolutions) is always tricky under linux, and I know that some drivers do it better than others, but I've never set this up before myself. Hopefully someone around here knows which kind of card this is easiest to set up on (ATI/Nvidia/Intel) and what sort of success other people have had with this.

---

### Post by tuxxy on 2008-08-13
nvidia! 

[http://ubuntuforums.org/showthread.php?p=1773584](http://ubuntuforums.org/showthread.php?p=1773584)

---

### Post by Perpetual on 2008-08-13
Thank you both for the amazingly fast responses.  I am leaning toward the DV6910US with the Nvidia card so tuxxy, thanks for the link!

Will do some more reading.

Landon

---

### Post by ericimboden on 2008-08-19
Hey Perpetual,

I'm looking at that same laptop (HP dv6910us).  I'm thinking of dual-booting since there are times I still need to use Win.  If you end(ed) up getting it, can you post a follow-up to let us know your thoughts?

Thanks!

Eric

---

### Post by shak541 on 2008-08-19
i would definatly say nvidia!!! i have a hp with 7150M and wow... easy... just sudo nvidia-settings. and set up... resolutions can be set differently for your laptop and external.. ive powered a tv at almost 3000 by something along with my laptop monitor at native 1280 800 and compiz fusion with a video running. my display was cloned and compiz worked. the video played on both internal and external displays and the cube and all would work great. this was with rain too. and it didn;t lag too much. extreamly useable in ubuntu. In vista.. well... your doomed. i couldd't even play need for speed carbon at the lowest and using ubuntu with cedega i could play with no lag at all, while vista wasn't even playable. i would definatly recommend the 7150M becasue it is surprisingly powerful in ubuntu. tell me if you need anymore info! :D

---

### Post by Perpetual on 2008-08-20
> **ericimboden said:**
> Hey Perpetual,

I'm looking at that same laptop (HP dv6910us).  I'm thinking of dual-booting since there are times I still need to use Win.  If you end(ed) up getting it, can you post a follow-up to let us know your thoughts?

Thanks!

Eric

It's been...ok.  I really like the laptop in comparison to my 5 year old Dell.  I went with the 6910us with the nvidia card and the Restricted Drivers picks the card up and installs everything.  Wireless has been another issue entirely.  You can make it work and there are numerous posts here about it (Atheros 5007).  I have had issues with suspend though and am going to try and work them out this evening.

Funny thing is, HP's specs say this laptop has an intel wireless card...I wish it did!  That was one of the reasons I bought this laptop but it's an Atheros.  I don't believe Intrepid is going to support Atheros out of the box but 9.04 should.  Some distributions are already starting to support this card.

If you buy it, let me know if you have problems.

Landon

p.s. I picked it up for $549 USD.  What are you paying for it?  Also, I think Vista runs very well on it.  This has been my first experience with Vista and to me, it seems like Vista has gotten somewhat of a bad rap...

Edit: I am not a gamer so I do not know how games play on Vista.  It is an integrated graphics card so i would think they would not play very well.

---

