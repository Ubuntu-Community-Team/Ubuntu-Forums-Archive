---
title: "Sudden lock-ups and reboots (kernel NULL)"
date: 2012-10-22
forum: Hardware
---

### Post by 6sl7g12xW4 on 2012-10-22
Hi all,

Since two weeks or so my system sometimes suddenly locks up (ubuntu 12.04). Meaning that I can see my screen, but mouse/keyboard doesn't work and when I press the power button (short) it doesn't suggest to shut down.
Other times it will just reboot randomly. Then when it starts up again it will hang on the boot check 9/10 times. 
So I think it's a hardware issue. 
I started off by running memtest86 from a livecd. It would also just randomly hang on 7% or so. So I started it again and another hang! But when it fully ran it said it passed all the test.
I recently (about a month or so ago) build in a SSD (the crucial M4, firmware 010G), so I thought maybe that's the culprit. But I just booted from a livecd and it still hang.....

Sometimes I get this screen: [http://i.imgur.com/AwcBD.jpg](http://i.imgur.com/AwcBD.jpg)
Maybe it's helpfull. 

I'm guessing i'll have to build a new pc, but if it's my SSD or a HDD which i'm going to reuse it still wouldn't solve the problem, but it would cost a lot of money....

So I hope someone can identify the problem. 

Thanks in advance!

---

### Post by SlugSlug on 2012-10-22
well if memtest is hanging I'd look at that

I've had faulty RAM pass on memtest a few times


A little test I do is slightly wobble the ram with OS loaded - if it crashes replace it :)

---

### Post by 2F4U on 2012-10-22
> I started off by running memtest86 from a livecd. It would also just  randomly hang on 7% or so. So I started it again and another hang! But  when it fully ran it said it passed all the test.

If memtest is hanging it is never a good sign and most of the time indicates that your RAM is faulty. If you have more than one chip in your system, subsequently remove them and see if it gets better.
Additionally, one run of memtest is not adequate. I once had bad RAM which showed up only on the second run.

---

