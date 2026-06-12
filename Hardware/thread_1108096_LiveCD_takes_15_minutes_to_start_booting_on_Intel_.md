---
title: "LiveCD takes 15 minutes to start booting on Intel I7"
date: 2009-03-27
forum: Hardware
---

### Post by hmjbarbosa on 2009-03-27
Dear all, very strange problem. I got a new machine with the following specs:

Intel I7 i920, MOBO Intel DX58SO
GeForce 8500GT
8Gb of DD3 RAM and 1Tb of SATA disk
LG DVD/CD writter connected to SATA

When I try to boot from an Ubuntu LiveCD the initial menu takes 10 to 15 minutes to show up. The system seems to be hanged in the mean time and not even keyboard LEDs respond do num-lock or caps-lock.

After this delay, the system shows some other regular bios messages on the screen and then the initial live cd menu appears. After this point, the cdrom is working normally and I can choose to try or install ubuntu. Installation goes very fast and the system is working fine.

Trying to read the liveCD from the installed ubuntu shows no delay. Moreover, trying to boot from the Vista or the OSX (ideneb and IPC) installation DVDs does not show the problem.

What I already tried:

=> cd's recorded in the same cdrom drive and recorded elsewhere
=> cd's recorded at minimum (4x) and maximum (48x) speeds
=> server, desktop, i386 and x86_64, for both 8.04 and 8.10

In all these cases I had to wait for 10-15 minutes for the first livecd menu to show up.

Any ideas what could be wrong? maybe the ubuntu live cd doesn't like a cdrom attached to SATA?

Thanks,
Henrique

---

### Post by albandy on 2009-03-27
Have you tried with other cd, mine don't work well with princo cd's but perfect with imation or verbatim

---

### Post by hmjbarbosa on 2009-03-27
Albandy,

I tried with Maxwell and Multilaser and got the same problem. Anyway, I don't think it should be that... I mean, why would the liveCD be read perfectly after the system is installed, but not during boot?


Thanks,
Henrique

---

### Post by albandy on 2009-03-27
Could be a problem between isolinux and your BIOS. Have you tested it with other operating systems?

---

### Post by hmjbarbosa on 2009-03-27
Yes I tried.
The Windows Vista Installation dvd starts immediately after I power on the computer. The same with Mac OSX installation dvds (tried both ideneb and IPC).
Only the ubuntu media hang for 15 minutes...

Question(possibly dummy): if ubuntu is compatible with my bios, why wouldn't the isolinux be?

Henrique

---

### Post by albandy on 2009-03-27
I don't know, but maybe it's the way isolinux works.

---

