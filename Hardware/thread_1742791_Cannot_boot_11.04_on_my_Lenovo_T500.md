---
title: "Cannot boot 11.04 on my Lenovo T500"
date: 2011-04-29
forum: Hardware
---

### Post by venturax on 2011-04-29
Hi guys,

Im kinda stuck here. I have tried to download 11.04 64bit and put in on a USB stick to try it out, but i dont get very far.

I see the end of a trace and then it just hangs there. seems to be related to the Radeon graphics card. Is i cant even get a terminal line to dump the trace log, i have taken a picture of it (i know... sooooo 80's :-) )

HELP please.. Im running my head against the wall here ](*,)

---

### Post by RattyC on 2011-05-01
Same for me on a T500, i thought i was going mad until i tried it on my MBP in Virtual box and it all worked fine.

---

### Post by RattyC on 2011-05-02
BTW, venturax what is the BIOS version on your T500? I am going to try updating mine. I will let you know how i get on.

---

### Post by RattyC on 2011-05-02
Seems to have improved things, i am now on BIOS 3.18 and i can get a purple screen rather than just white text.

I have also tried a fresh install of 10.10 and then an upgrade but that just boots to a purple screen as well.

---

### Post by antskip on 2011-05-02
I have no problems at all installing 11.04 through wubi on a W500. Runs brilliantly fast. I am going to trial it out for a while before considering doing a conventional install....

---

### Post by RattyC on 2011-05-02
Thanks antskip,

I think i have come to a compromise, if i explicitly select the shared graphics in the bios it allows me to get start the installation procedure.

I think this post is talking about the same problem:

[http://ubuntuforums.org/showthread.php?p=10751267](http://ubuntuforums.org/showthread.php?p=10751267)


It would be nice not to be stuck with shared graphics though.

---

### Post by venturax on 2011-05-02
Just a small update:
I just tried to boot an 10.04.2 LTS and it worked like a charm. Tried also with a 10.10, but it gave me a black screen :-(

Tried to boot 10.04 and then update to 11.04 and it was broken again :-k

It seems that the T500 is not officially supported by Ubuntu
[http://www.ubuntu.com/certification/make/Lenovo/laptops](http://www.ubuntu.com/certification/make/Lenovo/laptops)

I really hope that a solution is around the corner [-o<

---

### Post by venturax on 2011-05-02
> **RattyC said:**
> BTW, venturax what is the BIOS version on your T500? I am going to try updating mine. I will let you know how i get on.
Mine is 2.16, so its really old.

I tried your hint, only as a slight variation (as this is probably related to the bios version itself)

Set Config->Display->Graphics Device to Discrete Graphics (Switchable Graphics was previously selected)

Now save, exit and reboot..

Now it booted. I haven't tried to install any proprietary drivers to get hardware acceleration, so i don't know how deep the rabbit hole goes.

But it can be used as a workaround, so i mark the thread solved. The [thread]("http://ubuntuforums.org/showthread.php?p=10751267") you mentioned is more accurate, so i think we should participate there, if possible :-)

---

