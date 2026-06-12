---
title: "Can't get Hardy LiveCD to work on Toshiba Laptop"
date: 2008-08-26
forum: Hardware
---

### Post by fosron on 2008-08-26
I have Toshiba Satellite L350D. Im trying to load LiveCD, but i get error: *udevd-event[1405]: run_program: &#8216;/sbin/modprobe&#8217; abnormal exit* and after that Debian BusyBox is showed. I searched in google alot, nothing helped. Tryed several boot options. No luck. What could be the problem?. Im using ubuntu-8.04-desktop-i386 loaded with Unetbootin into my USB drive. I tried Wubi & CD too, but the same thing happend...

---

### Post by fosron on 2008-08-27
Could be the problem in the kernel itself?

---

### Post by CheeseEatingBulldog on 2008-08-27
I have had the busy box problem when making a usb boot disk, download another version of the livecd, or better yet grab the alternative cd and install from command line. You can solve the busy box error by editing one of the text files as I seem to remember, which isn't any help seeing as you have it on cd.

You could also try adding "irqpoll" to your grub boot line, which has solved boot problems for me in the past.

---

### Post by fosron on 2008-09-11
No, its not the problem. Well ubuntu 8.04.1 launched, but still it can't find the partitions on hard drive.

---

### Post by chayzer on 2008-09-16
So far I've figured out it has to do with the BIOS setting and the way it controls the SATA drives.. it is set to default "AHCI" which is apparently some sort of raid setting.. which would explain why I couldn't get XP to install on it.. and setting it to Compatibility mode hasn't helped yet either..

Intrepid Ibex likes this computer.. livecd, wireless ath9k... all works out of the box.. unfortunately it's got a bit of a ways to go before it's polished enough.. and yes I know it's a pre-release..

---

