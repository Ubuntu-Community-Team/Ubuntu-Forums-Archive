---
title: "LIRC with serial Lego IR Tower"
date: 2009-01-08
forum: Hardware
---

### Post by cujonz on 2009-01-08
After extensive searching, and finding no results, I've joined the forums to ask you all.

I'm trying to set up LIRC with a serial Lego IR Tower, seeing as I have it handy and it saves having to buy/build something to do the job. The device seems to respond to NQC, the LED lights up and NQC seems to be able to output to it on /dev/ttyS0 (I haven't tried it with the RCX as batteries aren't something I keep a stock of anymore).

Running the following makes the LED on the device light up, but obviously it doesn't work.
```
cujo@cujo:~$ irrecord --device=/dev/ttyS0 --driver=irman  ~/Documents/ir1.txt

irrecord -  application for recording IR-codes for usage with lirc

Copyright (C) 1998,1999 Christoph Bartelmus(lirc@bartelmus.de)

irrecord: could not open /dev/ttyS0
irrecord: irman_init(): Connection timed out
irrecord: could not init hardware (lircd running ? --> close it, check permissions)

```

lircd was not running at the time, and I've also tried other likely looking drivers, and running as root.

Running Ubuntu 8.10 with the latest version of lirc (the latest in the repositories).

So my question is this: Has anyone had success with the serial Lego IR Tower using lirc? Is there another driver I should be using?

If this isn't possible then I'll just have to build one myself, which isn't a problem.

Thanks.

---

### Post by cujonz on 2009-01-09
Bump.

Anyone at all?

---

