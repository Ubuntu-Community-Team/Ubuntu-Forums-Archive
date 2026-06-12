---
title: "[SOLVED] No visual effects or anything to do with graphic card"
date: 2008-08-22
forum: General Help
---

### Post by Viking007 on 2008-08-22
Hello Friends

About me: Complete noob about ubuntu and 8.04 (or Hardy as its sometimes referred) is the first ubuntu version for me....

Anyways I did the compiz check and got this:

```

v~$ compiz check
Checking for Xgl: not present.
Found laptop using ati driver.
aborting and using fallback: /usr/bin/metacity


```

and for Compiz-check:

```

:~$ compiz-check

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Radeon IGP 330M/340M/350M
 Driver in use:         radeon
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Laptop using radeon driver. 

Would you like to know more? (Y/n) y

 It has been detected, that you are running a laptop with an ATI chip.
 The radeon driver supports Compiz out-of-the-box but because of a nasty bug
 in the driver that causes X to freeze, this particular combination had to be
 blacklisted in Ubuntu "Hardy Heron".

 In case you already used Compiz successfully on Ubuntu 7.10 (Gutsy), it is
 safe to skip the blacklist. 

Do you want to skip blacklist checks by Compiz? (y/N)

```

As I am newbie any help whatsoever will be really appreciated!! cause I really want to enable the desktop effects which I can't; I know it might have been already resolved in some previous thread but a step by step instruction will be really helpful.....THANKS.....and you rock:guitar:

---

### Post by overdrank on 2008-08-22
Hi and welcome, you may look here
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by Viking007 on 2008-08-22
Thanks for atleast answering.....lol....anyways but i read some other posts where they say you shouldn't do the skip checks for some reason beyond my understanding.....could tell me what the "side effects" would be if I do skip the checks.....
once again thank you very much

---

### Post by armageddon08 on 2008-08-22
> **Viking007 said:**
> Thanks for atleast answering.....lol....anyways but i read some other posts where they say you shouldn't do the skip checks for some reason beyond my understanding.....could tell me what the "side effects" would be if I do skip the checks.....
once again thank you very much

I have compiz which runs 'out of the box'. So I really don't know much about skipping checks. But, when they are insisting....there must be something. Perhaps, doing that will make Compiz prone to crashes.

---

### Post by Viking007 on 2008-08-22
Thanks....I actually tried skipping checks.....and seems alrite...well at odd times i can see frames behind minimizing a window or so....
just one more question....how do i work them....like are there any special keys to see the effects (sorry might seem pretty dumb) but noob so i guess its allowed....also how do people have a funny looking dock i.e. like a mac dock lol.....Thanks once again if you can help me with this as well

---

### Post by Garratt on 2008-08-23
yea go system > preferences > compiz settings manager

if that isn't there then you didn't install correctly

change animations > enable desktop cube etc, play around youll get the hang of it.

---

### Post by Viking007 on 2008-09-17
Thanks Everyone!
after trying soooooooooooo many things it still isn't working:( so i guess maybe i can't use it! :(

---

