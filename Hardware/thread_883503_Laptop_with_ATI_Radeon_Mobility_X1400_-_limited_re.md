---
title: "Laptop with ATI Radeon Mobility X1400 - limited resolution"
date: 2008-08-08
forum: Hardware
---

### Post by insanedesio on 2008-08-08
Hello all, I've spent several hours and tried various different things to try to fix this problem with no luck.  I'm really hoping someone might be able to help me out.

Basically, I installed Ubuntu (8.04) on my laptop, which is a convertible notebook from Gateway.  The video card is a Radeon Mobility X1400 - I've got the latest ATI drivers installed (Catalyst 8.7).  I've been unable to increase my resolution past 1280x768 despite the numerous things I've tried (adding entries in xorg.conf doesn't do it, nor does using aticonfig --resolutions=0,1440x900,1280x768).  Does anyone have ANY idea what I might be able to do to get it up to 1440x900?  I know it supports that resolution because when I had Vista on it that's what it was.  This is the last thing I need to get figured out (as well as the tablet) before I have my Ubuntu setup working just as well as my Vista setup (MediaMonkey aside).

Help?  Anyone?  Thanks in advance to anyone who can offer any kind of input.  I'm also going be trying Kubuntu (to check it out) but I'm not expecting that'll make much difference; I was also thinking of trying out Gentoo, but I was hoping to postpone that for until I have all problems solved on Ubuntu.

---

### Post by spandanj on 2008-08-08
hey,

I don't have a clue how to help ya.

But, here's what I think. I have dell inspiron 6400 with same video card. I always used restricted ati driver provided by Ubuntu. Once I thought about switching to drivers provided by ATI themselves, but didn't do it. As of my experience with the restricted driver -- all works fine at 1280x800 except PIXELATED video on fullscren. I have been told that it is problem with OpenGl not being available for other applications since it is occupied by compiz.

Long story short: I would use Ubuntu's restricted driver for ati first.

---

### Post by insanedesio on 2008-08-08
Yeah, I tried both.  First I tried the one for which Ubuntu prompted me - which was available via Synaptic; resolution wouldn't go past 1280x768.  Then on a subsequent install I decided to go for the manual install of the "official" driver downloaded directly from ATI to see if that would help; it didn't.

Anyone else?

---

### Post by insanedesio on 2008-08-10
...is there really no one who might have had this problem or might know how to solve it?  The small resolution is pretty limiting since I now have to keep all my windows maximized...

I'm using a Gateway CX210S (similar to other CX-series) convertible notebook running Hardy.  I also can't get the tablet working, but that's for another time... I'd appreciate any help here.

---

### Post by mtbsoft on 2008-08-11
I'm afraid I can't suggest anything other than what spandanj said.  My Inspiron 9400 also uses the same card and I also simply switched on the restricted drivers at first prompt - bingo, 1920x1400.  I've also tried the installing the ATI drivers afterwards (separate partition) and that worked fine too.

Only thing I have to ask is, was this a clean install or an upgrade from 7.x?  I found the upgrade method fraught with problems for the graphics and would recommend the fresh install for any ATI box.

---

### Post by insanedesio on 2008-08-11
Clean install.  But I'm just an idiot, so ignore me.  It turns out that I had mixed up resolutions on two different laptops - it was the *other* one that could do 1440x900.  I found this out by finally getting fed up and putting Windows back on it (I can't say that I didn't appreciate how easy it was to get the pen working in Windows...); I checked the resolution and it was only 1280x768.  My brain is just not functioning these days.

Thanks anyways for all your help.

---

