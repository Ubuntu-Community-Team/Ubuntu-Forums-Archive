---
title: "NC6000 problems: brightness buttons don't work"
date: 2006-11-23
forum: Hardware &amp; Laptops
---

### Post by Zippo1000 on 2006-11-23
Hello,

it seems, as if Edgy supports my HP NC6000 worse than Dapper did.
Here are my observed problems:

1. The brightness buttons don't work anymore. In Dapper they worked without problems. I've read a bit in this forum and tried some solutions, but without success. It seems as if it has something to do with HAL, but I'm no expert.

2. Second Problem is, that the fan doesn't speed up after the notebook wakes up form standby. Therefore I was able to observe, that the CPU temperature reached 100 degrees CELSIUS. I think this really is a severe problem and that it should be solved. When I boot and shutdown normally, the problem doesn't occur.

I would be thankful for any help or tip

Zippo

---

### Post by Zippo1000 on 2006-12-11
Hi,

I want to answer my question by myself, because I think it would be helpful for anybody who has the same problem.

Unfortunately I only was able to solve the first problem.
Here's my solution:

I just installed the fglrx drivers for my ati graphics card. This did the job. First I didn't install it because I want to use Beryl for some testing.
I don't know, if this is the only thing one has to do to make the brightness buttons work, because I did some changes posted in this forum too.

Thanks to anyone who helped me ;-)

---

### Post by matt.fiscus on 2007-01-12
I am having the same problem with the fan not coming back on after resuming from a suspend with my nc6000.

I would recommend that you use XGL/fglrx rather than AIGLX/radeon setup for running Beryl.  I tried both methods, and XGL just worked better on the nc6000.  Not to mention, your brightness keys will work.

---

### Post by jimbo111 on 2007-02-14
Does anyone know if anything has been done about the fan not coming back on after the system is on Standby? I'm running ubuntu 6.10 Edgy Eft, kernel version is 2.6.17-11-generic....

Thanks

---

### Post by squantrill on 2007-02-21
Install the fglrx driver in place of ati fixed my problem

Section "Device"

        #BusID          "PCI:1:0:0"
        Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
        **Driver      "fglrx"**
        BusID       "PCI:1:0:0"
:guitar:

---

### Post by Zippo1000 on 2007-03-23
Hello,

I upgraded to Feisty Fawn, even if it isn't not released as stable yet.
This solved the problems with the fans after standby.

After a few month with Edgy and without standby I'm really glad to use Feisty.

Zippo

---

