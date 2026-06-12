---
title: "Lenovo laptop pitfalls?"
date: 2017-04-05
forum: Hardware
---

### Post by mchatzikos on 2017-04-05
Hi,

I am thinking of buying a new laptop.  The previous Linux laptop I bought was a Lenovo (back in 2007), I've been quite happy with it (still works), so I'm thinking of buying a Lenovo again.

There are many models nowadays with fancy features that work under Windows (which add to the price tag), but it is unclear if they work under Ubuntu.  My question is this: Are there any models to AVOID?  That is, are there any models with known pitfalls under Ubuntu (or Linux) in general, one need not bother with?

Alternatively, if there is a more solid laptop choice than Lenovo, I'd appreciate any pointers.  Suggestions of favorite retailers are also welcome.  (I've been out of the game for waaay too long.)

Thanks,

-m

---

### Post by mörgæs on 2017-04-06
If you want new stuff then the [list of certified hardware]("https://certification.ubuntu.com/") is a good starting point. For used hardware I suggest that you take a look at the sticky threads in the [hardware forum]("https://ubuntuforums.org/forumdisplay.php?f=332"). 

What happened to the old Lenovo? We could also try to speed it up if it's getting slow.

---

### Post by mchatzikos on 2017-04-06
The old Lenovo is still working, but it is harder to run software on it -- I only use for browsing, and as a terminal to remote servers, nowadays.

Here's some key info about the processor and memory:

```

$ less /proc/cpuinfo
model name      : Intel(R) Core(TM)2 Duo CPU     T7500  @ 2.20GHz
cpu MHz         : 800.000
cache size      : 4096 KB
cpu cores       : 2

$ less /proc/meminfo
MemTotal:        2019904 kB


```

So, in principle, I could upgrade the memory and that'd improve things.  Not sure that'd be enough to run a modern system on it, though.

In addition, the fan is being a bit loud, despite having cleaned it recently, but, again, I could replace that, too.

What do you think?  Could this system run 16.04 smoothly?

---

### Post by Bucky Ball on 2017-04-06
... and you could chuck an SSD in it and bingo. Guess it's a matter of adding up how much that will cost against the cost of a new machine. A hardware upgrade will probably be cheaper and you can use the SSD in future even if the motherboard dies (or replace the MB, of course :)).

---

### Post by mörgæs on 2017-04-06
> **mchatzikos said:**
> 
What do you think?  Could this system run 16.04 smoothly?

Yes, but not necessarily Ubuntu. Give it a clean install of Lubuntu and see if you are satisfied with the speed.

More advice in the link in my signature.

---

### Post by mastablasta on 2017-04-07
> **mchatzikos said:**
> 
Alternatively, if there is a more solid laptop choice than Lenovo, I'd appreciate any pointers.  Suggestions of favorite retailers are also welcome.  (I've been out of the game for waaay too long.)


some things changed since 2007.

Lenovo is still there, supporting linux on some models.

HP has a business line optionally preinstalled with SUSE linux. Ubuntu will work well on them. Obviously so will openSUSE.

Dell with it's business line (Vostro) as well as some Inspirons will come with Ubuntu preloaded. they also have a few high end options with ubuntu.

then there is this - a bunch of linux selling companies with good builds.[https://linuxpreloaded.com/](https://linuxpreloaded.com/)

Some ASUS work well on Linux.

---

### Post by bursaidr on 2017-04-08
I already using Asus because the temperature is stabil even when I'm using it 2 or 3 days without off.

---

### Post by mchatzikos on 2017-04-20
Thanks for the input everybody.  I ended up buying a Dell Precision 3520 (i7-7700HQ, 32GB RAM).  I need it for scientific calculations.
I will look into upgrading the old laptop too, at some point, as a testbed to test new distros on.  Thanks for that tip, too.

---

### Post by mchatzikos on 2017-04-26
The laptop just arrived, and it looks great. This is a quad-core i7-7700HQ machine at 2.8 GHZ, 3.8 GHz at turbo.

However, I am a bit surprised that the CPU speeds reported in /proc/cpuinfo are way below the advertised values:

```

$ cat /proc/cpuinfo 
processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 158
model name    : Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz
stepping    : 9
microcode    : 0x48
cpu MHz        : 900.000
cache size    : 6144 KB
....

$ grep "cpu MHz" /proc/cpuinfo 
cpu MHz        : 800.000
cpu MHz        : 900.000
cpu MHz        : 900.000
cpu MHz        : 800.000
cpu MHz        : 900.000
cpu MHz        : 900.000
cpu MHz        : 900.000
cpu MHz        : 800.000

```

The speeds seem to fluctuate with time.  I've seen some as high as 1500.000.  Half of these are hyperthreads.  I'm not sure if there's a straightforward way to compare actual VS advertised speeds.  A naive way would be to add pairs of these speeds (of those using the same physical core), but even then the sum would fall short of the advertised 2.8 GHZ.

[https://www.howtogeek.com/127950/how-do-you-calculate-processor-speed-on-multi-core-processors/](https://www.howtogeek.com/127950/how-do-you-calculate-processor-speed-on-multi-core-processors/)

makes it sound like you can't do this operation, though.

Any input on that?

Also, would you recommend using the turbo setting?

Thanks!

---

### Post by mörgæs on 2017-04-27
You have discovered how powersave works. When there is little load on the processor the clock frequency is turned down. 

If you never reach 2.8 GHz under heavy load it's not a proof that the processor is failing, it just means that another part of the computer is the bottleneck.

---

