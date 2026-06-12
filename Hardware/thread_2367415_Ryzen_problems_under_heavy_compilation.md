---
title: "Ryzen problems under heavy compilation"
date: 2017-07-29
forum: Hardware
---

### Post by pjssilva2 on 2017-07-29
There is a long thread in AMD support forum about people having problems with heavy, multi-threaded, compilation in Ryzen systems, see [https://community.amd.com/thread/215773?start=0&tstart=0](https://community.amd.com/thread/215773?start=0&tstart=0)

A special characteristic is that the problem is not that easy to trigger under normal loads. You may compile many things and not see it. So one may have a processor that is affected but may not not see it. Fortunately some smart people have created a simple script that always shows the problem in my system and in the systems of the other people of the thread. The script can be found in

[https://github.com/suaefar/ryzen-test](https://github.com/suaefar/ryzen-test)

You just have to clone the repository using git, move to the ryzen-test directory and run ./kill_ryzen.sh. It is a very simple script, it downloads gcc-7.1 source code into a vram disk and start #processors simultaneous compilation of it. If any compilation fails it writes a message in the console saying how long it took to get the failure. After a few minutes, the build in my system fails unless I turn off SMT. With SMT off it can take many hours, but still fails in less than one day.

Now, I would like to ask a hand from the fellow forum users. If you have a Ryzen system can you test it with the kill_ryzen.sh script? Let's say for one or two hours with SMT on. After that post here the result even if no failures happen. This may be a good way to find out how common the problem is. That is the reason that it is important to have both kinds of reports: failures and successful builds.

Obs: The kill_ryzen.sh is an infinite build loop, the easiest way to stopping it is rebooting.

---

### Post by niet-giftig on 2017-07-30
Worrying!
I am looking for a new build, and I was on track for Ryzen.

When I read in the AMD thread that the AMD representative writes that many people do not experience the behaviour I think "Come on"
Not that many users are using Linux, and only a few of them are using the GCC
But it is reproducible. and not a compiler issue from what I read.
Is Linux not a priority for AMD?

If there is a problem with the processor, then bits can fail under every circumstance.
But not so much response from AMD and they are vague about where to complain.
A new stepping?

I will wait a little longer before I buy a Ryzen.
Next to the memory & bios issues, this not what I expect from a new build.

---

### Post by pjssilva2 on 2017-07-30
The official position of AMD up to the moment in the Forum is:

1) They are looking at it.
2) They are reading the messages we post in the AMD forum.
3) Each one affected should open a support ticket (that may end with one RMA). A problem is that people with RMAed processors still face the same bug.
4) There is no inside information, they don't even confirm or deny whether they are able to reproduce the problem themselves.

Meanwhile the signals point to a large problem. Yesterday one of the persons in the AMD forum decided to test his son computer (I think he used a live usb stick to do it). It was also affected. There are also reports of problem on FreeBSD ([https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=221029](https://bugs.freebsd.org/bugzilla/show_bug.cgi?id=221029)) and DragonFly  BSD,  other distributions like Gentoo (for obvious reason, they build their whole system from scratch).

There are some news about a possible new stepping that would address out of core issues (like in the memory controller). From our experience in the thread we are facing either problems in the memory controler or voltage issues. So this may be the real solution. Who knows?

---

