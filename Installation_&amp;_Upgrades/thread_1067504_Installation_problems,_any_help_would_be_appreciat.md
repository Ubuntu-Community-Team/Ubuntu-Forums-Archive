---
title: "Installation problems, any help would be appreciated."
date: 2009-02-11
forum: Installation &amp; Upgrades
---

### Post by mr_anderson808 on 2009-02-11
I have an old Dell Optiplex (P4, 40gb IDE HDD & 256mb of RAM) that I am attempting to run Linux (Ubuntu) on as a headless server.

Originally installed Ubuntu 7.10 from an official CD, which was working really well. I turned the machine on several days later & after the African music theme played the computer stopped on the sandy coloured screen, other times it would have a black screen with coloured streaks & occasionally it would work properly (maybe 1 in 10 boots would start properly).

I ran all of the updates & it still would not work. I then downloaded Ubuntu 8.04 & installed it. The exact same problems occured.

When it did start 'properly' the display was often not entirely on the screen (22" LCD display, native resolution 1050x1680), or the resolution was wrong.

I have also tried an old version of Xandros, which works okay, but having troubles with the resolution. I also have no idea how to use Xandros.

memtest suggests memory is okay. Maybe a problem with the integrated graphics?


I would really appreciate any help. I have a relatively limited knowledge with computers (ie. prepare to dumb things down).

Thank you!!

---

### Post by cariboo on 2009-02-11
Your monitor is not being detected properly, if you update to 8.04.2 your problem should be resolved. 

If you are going to run the system as a headless server, there is no need to run a desktop. Have a look at [webmin]("http://www.webmin.com/"), it is a web based server administration suite.

Jim

---

### Post by mr_anderson808 on 2009-02-11
Thanks for your help Jim.

If I don't use a desktop does that mean I will have to use command lines?

That may be a problem as the only commands I know are: apt-get install... & sudo shutdown...


Again, thank you.

---

