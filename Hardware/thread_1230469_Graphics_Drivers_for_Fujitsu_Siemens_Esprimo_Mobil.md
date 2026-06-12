---
title: "Graphics Drivers for Fujitsu Siemens: Esprimo Mobile v5535 with linux 9.04?"
date: 2009-08-03
forum: Hardware
---

### Post by xadz on 2009-08-03
Hey, I have a Esprimo Mobile v5535 with newly installed linux on, my screen resolution is 1024x700 or something like that.  And my screen quality is certaintly not as crisp as my Windows 7.  I'm running Linux from inside windows on the Dual Boot.  And I had this problem before instlaling graphics drivers on w7.  However, I don't seem to be able to find any, and its giving me a headache. :/

Any links to Graphics Drivers for this would be collosuly appreciated. :D
Thanks Alot.
Adam.

---

### Post by xadz on 2009-08-04
Bump,
really need help. :/

:popcorn:

---

### Post by xadz on 2009-08-04
Bump.

---

### Post by Yellow Pasque on 2009-08-04
[http://ubuntuforums.org/showthread.php?p=7133694#post7133694](http://ubuntuforums.org/showthread.php?p=7133694#post7133694)

---

### Post by jstenbac on 2012-03-12
I installed Ubuntu 12.04 on Fujitsu Siemens Esprimo Mobile V5538 and as we read previously here the screen resolution options were 1024x768 and 800x600.
Tried a few different things but then I found this instruction and voala, it works! Now I have 1280x768 (16:10) resolution. Perfect!

>my solution for the resolution problem (only 800x600) on ubuntu >8.10 SiS 771/671 Fujitsu Siemens Esprimo V5535 :
>
>add to etc/x11/xconf.org to the Section "Monitor" 
>HorizSync 30-107
>VertRefresh 50-185
>
>

Boot and it works perfect.

Johan S

---

### Post by overdrank on 2012-03-12
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

