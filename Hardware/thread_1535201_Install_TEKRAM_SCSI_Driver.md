---
title: "Install TEKRAM SCSI Driver"
date: 2010-07-20
forum: Hardware
---

### Post by MartinusEx on 2010-07-20
Hi out there,
I'm thoroughly lost.

I installed lucid on a AMD machine.
The pc has a tekram scsi controller installed:
```
lspci
01:08.0 SCSI storage controller: Tekram Technology Co.,Ltd. TRM-S1040 (rev 01)

```
which uses as TEKRAM DC3X5 chip.
The controller is connected to a scsi scanner.

I got as far as downloading and extracting a rar archive "Dbv30drv.rar"
it contains a tar.gz archive  (source code) and an image "driver.img"
and a readme.txt which tells me to compile a new kernel and also a "how to".

I never had to do this so far, so I don't know nothing about the how to, risks and I fear to blow things up.

Well, my questions and request for help
1. is there a simpler method available and known (I could not find very much regrading this on the internet or even in this forum)

2. If no.1 has to answered NO, can anyone talk me through the process


thx in advance

Martin

---

### Post by sam1948 on 2010-07-20
Hi,
i searched a little and the only fix i found was a [_[COLOR="Blue"]kernel patch (2002 pretty old..)[/COLOR]_]("http://lists.debian.org/debian-devel-changes/2002/09/msg00464.html")
most advanced linux user had tried to build the kernel, it is not too complicated but it require being patient and have some programing skills (build knowledge to be precise).
I would recommend this solution for u only if u have time for learning session and the computer can be down for a few days.

**otherwise **
did u had any other distro installed on that computer?
try other distro's older ubuntu or ever rpm distros.
u can hope the bug was solved there somehow.
if non of them will work u will be able to start u'r learning.

---

### Post by MartinusEx on 2010-07-21
Hi Sam,

due to the link you postet I found the following:
[http://ftp.nl.debian.org/debian-archive/pool/main/k/kernel-patch-tekram-dc3x5/]("http://ftp.nl.debian.org/debian-archive/pool/main/k/kernel-patch-tekram-dc3x5/")

there one can find
```
[F] kernel-patch-tekram-dc3x5_1.38-1.dsc	09:29 09-12-07	615
[F] kernel-patch-tekram-dc3x5_1.38-1.tar.gz	09:29 09-12-07	134424
[F] kernel-patch-tekram-dc3x5_1.38-1_all.deb	09:29 09-12-07	140472
[F] kernel-patch-tekram-dc3x5_1.41-2.diff.gz	03:49 02-11-08	4723
[F] kernel-patch-tekram-dc3x5_1.41-2.dsc	03:49 02-11-08	633
[F] kernel-patch-tekram-dc3x5_1.41-2_all.deb	03:49 02-11-08	81780
[F] kernel-patch-tekram-dc3x5_1.41.orig.tar.gz	03:49 02-11-08	72788
```

I downloaded and installed (at least I downloaded, the rest was done by lucid..)
```
kernel-patch-tekram-dc3x5_1.41-2_all.deb
```

The installer did the rest as said and the SCSI controller AND the scanner where immediately recognized and usable (simple scan)

The scanner is a vintage Microtek Scanmaker E6

Seconds..Sam not Days :popcorn:

Thx so much

Martin

---

### Post by sam1948 on 2010-07-21
Hi,
I'm glad to hear that(:
any way,
I would recommend **not to auto** install kernel updates, 
and just in case keep a copy of that deb file.

regards

1 more ..
about days, luckily u found a deb file which is ready to install, kernel patches are not always comes like this, mostly the required to rebuild the kernel. 
u were lucky this time(;

---

### Post by MartinusEx on 2010-07-24
Hi Sam,
i ear you are quite right.
Jep, i safed the deb file.

and..

the ISDN Card still is to install and here it looks like i need to go the hard way.

Let's wait and see..
This might be another thread and I'll get back to you.

Thx so far

Martin

---

