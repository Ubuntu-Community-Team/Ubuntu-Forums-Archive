---
title: "Processor woes"
date: 2007-08-19
forum: Hardware &amp; Laptops
---

### Post by chimerical_brio on 2007-08-19
Alright, so this will seem a bit cracked out, but bear with me. I know nothing about computer hardware.

I put together a computer using some parts that I got from a friend, and then I didn't use it for a few months. Now, though, I want to use it full time. I'm running Ubuntu Feisty, works fine it's just...a bit sluggish. I only have 512 MB RAM, so I figured that was the problem, but then I checked my CPU settings just to be sure, and it turns out that the processor is not a 2.56 GHz Pentium 4 as I thought, it's a 1.7 GHz Celeron.

I don't need to do a lot with my computer, just internet, email, word processing, the usual. But it's sluggish doing even that, and I'd really like it to be fast enough that I don't notice it at all. So the question becomes: will upgrading the RAM (which I know I need to do either way) be enough, or should I get a new processor? And if I do get a new CPU, what one do you recommend? Thanks.

---

### Post by w4ett on 2007-08-19
It's not really the processor speed that is slowing down the system, but more to the fact that the celeron CPU has limited cache memory in the CPU itself, which reduces the number of instructions it can process per clock cycle per second (that is the technical explaination)

Now for the non-geek response....IMO, adding an extra 512 Mb memory will help you out a lot, and unless you are going to do a lot of graphics intensive applications, anything more is overkill.  You haven't mentioned anything about a graphics card, but bear this in mind, just about any $30 Nvidia or ATI card will blow away any onboard graphics you may or may not be using, so that is another area in which you can make a big difference in system performance.

There is plenty of life left in that CPU, but you can get a Pentium 4 in the same socket configuration on Ebay or [www.pricewatch.com](www.pricewatch.com) for $30 which will also speed things up a bit.  I've run Beryl and Compiz on 1.5 Ghz Durons with a semi-decent GFX card and 512MB Ram.

---

### Post by davidsrsb on 2007-08-20
Ubuntu is very sensitive to hard disk access speed. Use hdparm to measure your transfer rate. Modern drives manage 50MB/s or better.

---

