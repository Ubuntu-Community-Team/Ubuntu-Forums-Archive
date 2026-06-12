---
title: "Acer Aspire 8935G"
date: 2009-11-09
forum: Hardware
---

### Post by mrkazoodle on 2009-11-09
Hi

I installed Ubuntu through wubi on my laptop, but it failed to recognize my network card (Broadcom NetLink BCM5784M).
(both 64 an 32 bit version)
Is this because I installed it through wubi or do I need to install their [driver]("http://broadcom.com/support/ethernet_nic/netlink_k57.php")?

If I need to install their driver, which one do I need to install?
I guess it's the linux (tg3) file I need to download, but in there there are 2 .tar files and an rpm, which one is the appropriate one?(btw: what does 'tg3' mean?)

ubuntu 9.10
Intel Q9000
4 GB RAM
ATI Mobility Radeon HD 4670

---

### Post by darkshadow on 2009-11-09
That is strange, I have a 8940G which uses the same card and it worked out of the box. 9.10 64bit

Yes lshw shows the driver handling it as "tg3" so maybe try manually loading it with "sudo modprobe tg3"

---

### Post by mrkazoodle on 2009-11-10
It didn't work, I'm going to retry to install the driver and if it doesn't work on the 32bit I'm going to try to install it on the 64bit version

Are you sure it isn't wubi related, if it worked on your laptop it should work on mine as well.

---

### Post by mrkazoodle on 2009-11-11
I installed the driver in both 32 64 bit editions, but no success.
My next step will be to install 9.04.

---

### Post by JBAlaska on 2009-11-11
Check this [Post](http://ubuntuforums.org/showthread.php?t=1288865) and see if that soloution works for you.

---

### Post by mrkazoodle on 2009-11-11
my card isn't a wireless card but maybe it might work, I'll check it later

Installing 9.04 (still using wubi) fixed the problem temporarily, until I installed numlockx, the ATI driver and a whole bunch of updates, now I can't even boot anymore :(
It asks for my user name and password (but in command line mode!)
and then it gives me a screen with gray lines, some red 'dots' and 2 green ubuntu icons

---

### Post by mrkazoodle on 2009-11-11
I reinstalled 9.04 (still wubi), installed numlockx again and updated it, now it runs perfectly fine.
conclusion: The problem is 9.10 related, so I hope it is going to be solved in the future.

---

### Post by mrkazoodle on 2009-11-15
It doesn't run as fine as I thought, My network connection is working, but the downgrade to 9.04 broke the sound, I can't play any song.

I've opened up another thread:
[http://ubuntuforums.org/showthread.php?p=8314487#post8314487]("http://ubuntuforums.org/showthread.php?p=8314487#post8314487")

---

### Post by unknownofflineuser on 2010-02-10
install newer kernel. see here - [http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g](http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g)

---

### Post by mrkazoodle on 2010-05-03
> **unknownofflineuser said:**
> install newer kernel. see here - [http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g](http://ubuntuforums.org/showthread.php?t=1353041&highlight=8935g)

I didn't want to do that, so I waited until Lucid, now sound and Internet work fine. If I'd only get the brightness control to work. (there are numerous posts on that subject, so many one doesn't know where to start plus I have an ATI, god I wish it were a nVidia)

---

