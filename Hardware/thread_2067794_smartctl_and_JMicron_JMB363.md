---
title: "smartctl and JMicron JMB363"
date: 2012-10-07
forum: Hardware
---

### Post by AngelicLiar on 2012-10-07
Hey all,

I couldn't get smartctl to show full details on some of the disk drives I use, and have narrowed the problem down to them being connected via the motherboard's integrated JMicron JMB363 controller.

However, on their site ([http://www.jmicron.com/Driver.htm](http://www.jmicron.com/Driver.htm)) they state that their driver has been integrated into the kernel since 2.6.18 (I'm using 12.04 server, so kernel 3.2.0).

I can't use the other controller on my motherboard because I have 10 drives and need all the ports...

Any advice on how to get S.M.A.R.T to work?

Edit: The drives work properly and I can access them, I just can't get S.M.A.R.T data.

---

### Post by ahallubuntu on 2012-10-07
You need to issue options to smartctl - try the ones listed here:

[http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices](http://sourceforge.net/apps/trac/smartmontools/wiki/Supported_USB-Devices)


Try for example adding one of these options to the command:

-d sat

or

-d usbjmicron

You may also need to add 

-T permissive

---

### Post by AngelicLiar on 2012-10-07
Tried the options.

-d usbjmicron doesn't work at all.

-d sat gives the same result as without -d: SMART support shows as "Disabled", and stays disabled even if I enable it with -s on (however when I use -s on I do get a tiny amount of data. If I move the drive to a different controller, I get a lot more).

-T permissive and -T verypermissive do not help either.

I saw someone somewhere on Google blame a cable for this; could this be the issue (considering I'm not experiencing any visible data access problems to the disk)?

---

### Post by ahallubuntu on 2012-10-07
I fail to see how it could be a cabling problem if the drive otherwise works fine.

Assume you tried -d options AND -T permissive at the same time?

Have you tried installing a newer version (5.43) of smartctl from the tarball?  Is that newer than the latest Ubuntu version? I have built newer versions from scratch before to get around issues like this.

---

