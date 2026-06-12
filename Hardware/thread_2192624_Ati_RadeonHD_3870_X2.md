---
title: "Ati RadeonHD 3870 X2"
date: 2013-12-08
forum: Hardware
---

### Post by spook42088 on 2013-12-08
ok guys someone please help me out, im no so new to ubuntu now do i know every thing about it,
 i switched from windows after a series of bad updates corrupted the OS
so heres my issue, i reciently reinstalled ubuntu 12.04 LTS but am having problems
and i havn't encountered any thing like this yet, ive been using the radeon HD 3xxx series cards for
a couple years now and never had any problems however! (problem~~~~>)now that im running the 
3870X2 i can't get the drivers or catalyst to install, the ubuntu sees the card for what it is but as soon
as i try to use the catalyst PPA or the recomended  install method it says theres drivers for the card
but as soon as that appears it tells me no drivers can be found for this card . has any one delt with this
im super tired of  banging my head on a wall tryen to figure this out. has any one delt with anything like this?
PLEASE HELP!!


system specs(soon to upgrade)
ubuntu 12.04 LTS
320 Gb sata hdd
350 Gb sata hdd
asus m4a78- plus (great montherboard)
single core amd 2.3 gig proc ( gonna upgrad to phenom II x6 soon)
2 gigs of ram 667 mhz ( gonna add 4 more gigs)
Ati RadeonHD 3870 X2 ( my problem)

---

### Post by QIII on 2013-12-08
Hello!

If you are using 12.04.2 or 12.04.3, then you will not be able to use a proprietary driver for that card and will have to continue to use the default open source Radeon driver installed when you installed Ubuntu.

Unfortunately, ATI decided to stop Linux support for that card (all cards prior to the HD 5000 series, in fact) and the last version of Ubuntu that is supported by ATI is 12.04.1.  If you try to look for it, you will not find it in Ubuntu's repos, which is why you can't find it.

Although there are hacks and you may get a suggestion to use one of them, I would highly recommend against that course of action.  It effectively breaks you Ubuntu install.

Just use the open source driver you are using just as you did when you first installed.  Nobody in the Linux community can do anything to change ATI's mind about supporting versions past a certain point.

Cheers.

---

### Post by spook42088 on 2013-12-08
it's 12.04.3  and thats kinda what i was wondering about it, and would it really make that much difference just after reinstalling? was working just fine till my promary hard drive died then i reinstall and am having all kinda of issues

---

### Post by QIII on 2013-12-08
You would have problems from the get-go with 12.04.2 or later.  12.04.1 would have a proprietary driver available in the repo.  However, more recent proprietary drivers downloaded from ATI would still not work.

If it were me, I would: either install 12.04.1 and use the (nearly two year old) proprietary driver from the repo;  or install a later version and use the default open source driver.

Straight up Ubuntu is supported until April of 2014, which gives you some time to gather your pennies to purchase a card ATI still supports.

This is not going to change.  OEM's write drivers, not OS perveyors (Microsoft doesn't either.  Interestingly, if you install the ATI driver on a machine with an HD 4000 or earlier card, you will get the "Legacy" driver.  However, Windows doesn't have the wrinkle of X Server like Linux does, so you wouldn't notice.)

---

### Post by spook42088 on 2013-12-08
been kicking around the idea of getting a couple new vid cards, guess this makes my decision for me maybe a couple 5770's or 6770's :) a single core graphics card just dont cut it lol

---

### Post by Yellow Pasque on 2013-12-09
> **spook42088 said:**
> guess this makes my decision for me maybe a couple 5770's or 6770's :) a single core graphics card just dont cut it lol

A single, higher-powered GPU would be much better, or if you must have two GPU's, consider Nvidia SLI over AMD Crossfire...

---

