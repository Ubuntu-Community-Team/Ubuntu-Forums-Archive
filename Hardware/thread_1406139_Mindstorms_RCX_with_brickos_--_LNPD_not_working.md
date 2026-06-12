---
title: "Mindstorms RCX with brickos -- LNPD not working"
date: 2010-02-13
forum: Hardware
---

### Post by rodrigo.toste.gomes on 2010-02-13
Hello.
I'm new to robotics and recently bought a Mindstorms RCX kit that I found at a good price (about 80$, new! a local store was selling things they had had on stock for a long time).
The first thing I did was to look for something that would allow me to interoperate between linux and my new kit, and program in C. I found brickOS, installed it, and it works great, and I love it.
However, today, I found a problem.
I'm trying to control the brick through my computer, and the best thing I found for that appears to LNP (LegOS Network Protocol, I believe). So, I installed lnpd and liblnp in my linux computer.
However, it's giving me an error, and lnpd doesn't start!
The log file is as follows:

         0:Info > created lock file /var/lock/LCK..ttyUSB0
         9:Fatal > Invalid argument.  ioctl[TIOCGSERIAL](),rcxtty.c,line 154

I'm using a serial IR tower, connected to my computer through a serial to USB cable.
I have Ubuntu linux, 64 bit.
I've tried both compiling from source and installing the package in the repositories, and both gave me the same error.
I've tried starting lnpd with the --nolock option, and same error happened.
After searching thoroughly through the web, the best explanation I could find to what is happening is that the USB to serial driver may not support the TIOCGSERIAL (I found a patch that solved that). However, my computer is fully updated, and the patch I found is for an older version of the linux kernel.
Anyone knows what I should do?


Thank you for your time.
Rodrigo

---

### Post by tom.clabon on 2011-05-27
Hi,

Did you ever solve this?

I have just got my old mindstorms set off my parents and was thinking of doing what you were trying - controlling it from my PC. I also have 64-bit Ubuntu and it's the most up to date (I guess that's a bit more up to date than when you first posted :-) )

I have an old serial cable for it somewhere, probably in the garage, but I need to find it. I then need to buy a serial adapter or buy one of the USB cables that came with the later sets. What I buy might depend on how you got on

---

### Post by rodrigo.toste.gomes on 2011-06-01
I gave up on using lnpd.
However, I managed to control it from my computer through the use of a library named lnphost:
[http://lnphost.sourceforge.net/](http://lnphost.sourceforge.net/)
Good luck!

---

