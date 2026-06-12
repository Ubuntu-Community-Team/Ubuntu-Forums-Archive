---
title: "Jaunty/9.04 is killing my battery life"
date: 2009-08-18
forum: Hardware
---

### Post by rosen561 on 2009-08-18
specs:
HP Pavilion dv9925nr
AMD Turion 64 X2
Nvidia GeForce Go 7150M
Ubuntu Jaunty 9.04


Hello,

I had a good run with Hardy and finally decided to upgrade before school starts. I've noticed a few issues with it, but this could become the third strike that forces me to switch back to Windows, at least until things get worked out in Ubuntu.

Here's the deal. I did a clean install of Jaunty (totally removed hardy, resolved the hard drive, then installed 9.04). Just after the install I was surprised by an *increase* in battery life to just over 3 hours--a good thing. However, over the past couple weeks, the battery life has been steadily decreasing, down to 2 hours now, though I think it depletes faster. This seems ridiculous considering my Vista half tells me I have 3 hours and 20 minutes (on power saving mode,) and I believe it. 

I have read other threads showing others are having similar issues, which is a bad sign for the developers. I think my problem is stemming from both CPUs running at or greater than 50%  a lot of the time, even with no windows open, and I have no idea why. I tried the idea I read about using the panel's CPU scaling monitor, but it says both cores are 'ondemand', yet the System Monitor shows both are running hot. 

Please help. I like Ubuntu, I like its features, I love the boot time, but don't like its current issues and am dissappointed by my "upgrade".

Thank you all.

P.S. if you have suggestions, my other issues:
Unable to suspend 
Can't shutdown/boot unless plugged in, or if not plugged in, must push a key
When not plugged in, can't shutdown without turning off WIFI card

---

### Post by utnubuuser on 2009-08-18
Does this info apply to Hardy Heron (the LTS release) as well, or is this only an issue in 9.04?  - (9.04 is essentially Debian Sid - unstable).

---

### Post by sergiom99 on 2009-08-18
> **rosen561 said:**
> 
P.S. if you have suggestions, my other issues:
Unable to suspend 
Can't shutdown/boot unless plugged in, or if not plugged in, must push a key
When not plugged in, can't shutdown without turning off WIFI card

I would definitely start by fixing this: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051)

Worked like a charm in mine.
Also, read the whole thread and add your info to the bug reports in Launchpad, so that they fix this DSDT thing.

---

### Post by rosen561 on 2009-08-18
These issues are only jaunty.

---

### Post by Jon Monreal on 2009-08-18
You could try the "Powersave" setting on the CPU scaling monitor. This should run your processor at the lowest clock possible, which may help to save power.

Also, have you ever looked into how accurate those estimates are? It can be hard to tell unless you time it out.

> **rosen561 said:**
> These issues are only jaunty.

While I hate to say it, if things don't work out, perhaps you should just "downgrade" to Hardy. It is a LTS release, after all, and it's not like there is a requirement that one has the latest release. You could then test 9.10 when it comes out using a Live CD to see if things work better in Karmic.

---

### Post by rosen561 on 2009-08-20
> **Jon Monreal said:**
> You could try the "Powersave" setting on the CPU scaling monitor. This should run your processor at the lowest clock possible, which may help to save power.



I left the cpu scaling at on demand, however, I turned compiz effects off, as I saw suggested in other threads, which has simmered down the CPUs entirely. Waiting to see how it effects the battery life.

---

### Post by Jon Monreal on 2009-08-20
> **rosen561 said:**
> I left the cpu scaling at on demand, however, I turned compiz effects off, as I saw suggested in other threads, which has simmered down the CPUs entirely. Waiting to see how it effects the battery life.

Yeah, I don't use Compiz on my laptops, and when I'm doing something that does not require much power (such as word processing), I set my laptop to powersave. The system still seems greatly responsive @800MHz, although I wouldn't use Powersave for anything but everyday tasks such as web browsing and word processing.

---

