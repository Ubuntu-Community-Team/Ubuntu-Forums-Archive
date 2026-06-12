---
title: "mouse input being dropped"
date: 2015-03-17
forum: Hardware
---

### Post by tcll5850 on 2015-03-17
I've posted a question a few days back on askubuntu which has yet to be answered...
[http://askubuntu.com/questions/597041/ubuntu-randomly-dropping-my-mouse-how-can-i-stop-this](http://askubuntu.com/questions/597041/ubuntu-randomly-dropping-my-mouse-how-can-i-stop-this)
it's currently happened 4 times since I posted.

my keyboard works fine, but USB mouse support seems to be completely dropped at random and nothing seems to fix it...

I've just tried downdating my kernel to *-43 (from *-46) in attempt to prevent the issue, though I doubt it'll really have much (if any) effect...

can anyone here help me??

---

### Post by dino99 on 2015-03-17
is there something usefull logged ? (syslog dmesg xorg.0.log other /var/log/*)

---

### Post by pqwoerituytrueiwoq on 2015-03-17
wireless usb mouse? sometimes they do wear out, could be cat hair in it
can you test a alternate mouse

---

### Post by tcll5850 on 2015-03-17
@pqwoerituytrueiwoq:
> 
I've tried:
- reconnecting my (wired) USB mouse (mouse never turns back on)
- connecting another USB mouse (mouse never turns on)
- $ compiz --replace (this completely borked everything)
- $ compton --replace (nothing changes)


@9d9: I'll take a look next time it happens...
I needed to reinstall my VBox drivers and a slew of other things after downdating my kernel, so it's a bit pushed back atm

EDIT:
of course it hasn't happened since the report XD
when you want things to happen, they never do :P

---

### Post by tcll5850 on 2015-03-26
alright so apparently it acts up when Minecraft eats all of my RAM and goes into my swap.

after I close, the DNS Tech Pack doesn't clear itself from my memory and thus I can't do much of anything until I restart.
(killing Java creates a zombie process with the RAM still used)

so it happened just last night, so I had to hard shut down before going to bed
(Power button does Hibernate, so I need my mouse to shut down)

can't upload attachment here (invalid file), using copy instead:
[https://copy.com/4Hn1ICmDpapBgphP](https://copy.com/4Hn1ICmDpapBgphP)

anything else needed??
I'm not sure how XFCE, xfdesktop, xfwm, compton, or numix, and the like manage my mouse...

---

