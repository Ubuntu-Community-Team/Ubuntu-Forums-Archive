---
title: "cpufreq ignore beryl"
date: 2007-03-26
forum: Hardware &amp; Laptops
---

### Post by peibol on 2007-03-26
Hi there, since I just installed beryl, the first thing I realize is that the proc keeps running at full speed because beryl process is working all the time painting the screen. So i was wondering, is there a way to tell cpufreq to ignore a process? beryl in this case.
I'm asking because I don't like to have the proc at full speed raising temp in the laptop.

Regards.

---

### Post by kidders on 2007-03-26
Hi there,

> **peibol said:**
> is there a way to tell cpufreq to ignore a process?Not afaik, but you could try altering the CPU usage thresholds ... depending, of course, on what your CPU usage is like when your machine is sitting there doing nothing.

In any case, forcing your computer to use a lower CPU frequency than it "should" *may* adversely affect Beryl's performance, but there's only one way to find out!

---

### Post by peibol on 2007-03-26
> **kidders said:**
> Hi there,

Not afaik, but you could try altering the CPU usage thresholds ... depending, of course, on what your CPU usage is like when your machine is sitting there doing nothing.

In any case, forcing your computer to use a lower CPU frequency than it "should" *may* adversely affect Beryl's performance, but there's only one way to find out!

Yes, that could be one way to do it, but not the best. I was just wondering.
Anyway, I don't think I'll keep on using beryl.

Thanks anyway.

---

### Post by kidders on 2007-03-26
> **peibol said:**
> Yes, that could be one way to do it, but not the best.Yes, it wouldn't exactly be ideal. As you seemed to suggest, the best advice would probably be to stop using Beryl, since it swallows up so much of your CPU time. :-( I can't really use it either ... but that's only because I'm a cheap-skate and never buy good graphics cards!

I'm not the right person to help you with tweaking Beryl, but before you kill it, it may be worth double-checking whether you can tweak it (or maybe just turn off some of the more demanding features) to make it less hungry.

---

### Post by peibol on 2007-03-26
> **kidders said:**
> Yes, it wouldn't exactly be ideal. As you seemed to suggest, the best advice would probably be to stop using Beryl, since it swallows up so much of your CPU time. :-( I can't really use it either ... but that's only because I'm a cheap-skate and never buy good graphics cards!

I'm not the right person to help you with tweaking Beryl, but before you kill it, it may be worth double-checking whether you can tweak it (or maybe just turn off some of the more demanding features) to make it less hungry.

Nah, it's not a performance issue, it runs just fine, but since beryl is working all the time, and it's a front process, cpufreq assumes it needs power (and doesn't), so it keeps cpufreq working at full throttle even when it's doing nothing.
I don't know, but I gess there should be a way to ignore it (or maybe start it as a service or someting like that) so cpufreq doesn't pay that much attention to it.
The graphic card is an Ati X700 and has way more than enought brute force. It's just the full throttle all the way down issue which I don't like.

---

### Post by kidders on 2007-03-26
Hmm...

What would happen if you reniced it, I wonder? Would that make any difference?

---

### Post by peibol on 2007-03-26
> **kidders said:**
> Hmm...

What would happen if you reniced it, I wonder? Would that make any difference?

Well, that was a good question... I'll try it this afternoon at home and post it back.

Thanks

---

### Post by s0cket on 2007-03-26
> **peibol said:**
> Nah, it's not a performance issue, it runs just fine, but since beryl is working all the time, and it's a front process, cpufreq assumes it needs power (and doesn't), so it keeps cpufreq working at full throttle even when it's doing nothing.
I don't know, but I gess there should be a way to ignore it (or maybe start it as a service or someting like that) so cpufreq doesn't pay that much attention to it.
The graphic card is an Ati X700 and has way more than enought brute force. It's just the full throttle all the way down issue which I don't like.

I would of thought an X700 would have enough power to keep most of the load OFF the CPU.  I have a GeForce Go 6300 and my Beryl idles around 5-8% CPU usage and that doesn't ever change much regardless of what I'm doing.

---

### Post by peibol on 2007-03-26
> **s0cket said:**
> I would of thought an X700 would have enough power to keep most of the load OFF the CPU.  I have a GeForce Go 6300 and my Beryl idles around 5-8% CPU usage and that doesn't ever change much regardless of what I'm doing.

Yes, it should be that way, actually the X700 keeps the work off the main CPU, but not the beryl process itself. Maybe it's an Ati issue (since you have a nvidia), or maybe it's something about the driver, but the thing is: 
beryl running = cpufreq at full throttle; 
beryl !running = cpufreq idleing

I'll try to renice it tonight and post the results.

---

