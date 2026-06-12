---
title: "Odd Bootchart results on netbook - any ideas?"
date: 2009-01-30
forum: Hardware
---

### Post by gcogger on 2009-01-30
Hi,

I'm using Ubuntu Netbook Remix (8.04) on a Toshiba NB100 netbook, but it seems to take longer than expected to boot.  I've performed a 'profile'd boot and set Concurrency to 'shell' in one of the config files, which together have shaved 10 seconds off the boot time.  It now, from pressing the power button, takes 73 seconds to get to the login prompt and a further 35 seconds (after entering the password) until the computer is usable.  That's longer than I would have expected.

I tried installing Bootchart to tell me what was happening, but that is where the confusion arises.  The chart produced seems reasonable, but only accounts for 42 seconds of time.  That leaves a further 31 seconds unaccounted for before I can log in.  Does anyone have any idea what might be happening in all that extra time?

Cheers,

Graeme

---

### Post by vmalep on 2009-02-13
As for me, I have dual boot with the original Ubuntu remix 8.04 and the Ubuntu remix 8.10. I noticed that the Ubuntu 8.10 interrupts the boot for a while trying the configure the network at some stage (I noticed that by switching to the prompt during the boot: alt + F9 I think).

I removed the link S35networking in /etc/rc0.d but with no success yet.

---

### Post by binbash on 2009-02-13
can you add the bootchart picture as attachment please?

---

### Post by vmalep on 2009-02-13
Here they are. Very interesting tool!

It allowed me to accelerate the boot of the ubuntu 8.10 alternate lpia version by removing the link S40Networking in /etc/rcS.d

Hope those charts will be helpful to you...

---

