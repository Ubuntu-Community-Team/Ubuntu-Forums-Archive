---
title: "cpu usage EVERY PROCESS has gettime errors"
date: 2012-03-01
forum: Hardware
---

### Post by provoko on 2012-03-01
I'm noticing gettime errors in every process, usually browsers, but also Xorg and compiz.  I'm running latest ubuntu 11.10 32bit.

So an strace on **ANY** process reveals gettimeofday and clock_gettime errors with the following message: **"Resource temporarily unavailable"**.

I first noticed this when midori would randomly go 100% cpu, so, I stopped using midori, then I noticed firefox doing it sitting around 20% cpu usage for no reason (literally 1 tab about:blank).  Then I straced every process on the OS and discovered the same problem with everything.

What is going on?

Specs:
unbutu 11.10 32bit
asus UL20a

Thanks.

---

