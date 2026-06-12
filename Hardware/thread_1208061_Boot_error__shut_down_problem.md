---
title: "Boot error / shut down problem"
date: 2009-07-08
forum: Hardware
---

### Post by tamerucar on 2009-07-08
Hi all,

I have Ubuntu 9.04 installed on my Toshiba Tecra S10-11A laptop. I have two strange problems. First one is:
When booting, I got this error twice:
```
ata2.00: failed to set xfermode (err_mask=0x4)
```
But, it continues and boots. Is this something serious?

The second problem is: when I try to shut down, my computer stucks at this line:
```
CPU0 attaching null sched-domain 
```

What should be the problem?

Thanks for your help.

---

### Post by tamerucar on 2009-07-09
Any idea :icon_frown:

---

### Post by tamerucar on 2009-07-09
Hi again,

After a little web search, I eliminated the "shutdown freeze" issue by booting the kernel with **acpi=on** parameter.

But, I still have no clue on the "startup error message" which is
```
ata2.00: failed to set xfermode (err_mask=0x4)
```

:(

Note: This error does not block booting but it makes boot time longer than it is and seeing it on every boot annoys me a little bit... :-s

---

### Post by Drizzt124 on 2009-07-12
I own a Tecra S10 and I experience the exact same problem. Posted a link about it, supposedly had to add irqpoll line at the end of kernel line in "menu.lst" but it's not working for me.

Problem booting (xfermode problem), problem shuting down and of course no cd/dvd drive detected unless I boot with a ubuntu liveCD in my drive (but I boot from HDD, well I think).

I'll keep you posted if I ever find a solution.

Good luck,
Max

---

### Post by tamerucar on 2009-07-13
Hi Max,

I also instructed to add irqpoll parameter but it didn't work for me either. Besides this problem, I'm having a brightness issue and I wrote a question about it here:
[https://answers.launchpad.net/ubuntu/+question/76698](https://answers.launchpad.net/ubuntu/+question/76698)

As a result, I managed to fix shutdown problem. But brightness issue, no cd/dvd drive detection and startup error makes Ubuntu useless for me. I hope, I could find fixes for those as soon as possible.

---

### Post by Drizzt124 on 2009-07-13
Hey, I don't know why but when I leave a cd while I boot (right now it's a cd with pictures only), well it boots all right, detects cd/dvd drive and shuts all right as well. I don't understand why but still, works more or less. Didn't have to add acpi=on line on the kernel.

Any idea why? Did you try it on your side?

Max

---

### Post by tamerucar on 2009-07-14
Yeah, it also worked for me too. It is interesting... What can cause the booting and shut down problems go away when booting with "any" CD?
 
By the way, this strange "Leave CD in drive" fix has no effect on brightness issue. I still can't control my laptop screen's brightness...

---

### Post by tamerucar on 2009-07-18
Hi all,

I found a solution for my case for the following error:

```
ata2.00: failed to set xfermode (err_mask=0x4)
```

I updated firmware of my DVD drive. And the error is no more.

---

### Post by Drizzt124 on 2009-07-30
Thx for the update, does work now with firmware update.

But like you, brightness switch does not work (fn keys at least).

I can change my brightness though using nvdia proprietary program (in the screen config windows).

Hope it helps!

---

