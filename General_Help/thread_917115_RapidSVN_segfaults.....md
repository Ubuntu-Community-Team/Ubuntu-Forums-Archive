---
title: "RapidSVN segfaults...."
date: 2008-09-11
forum: General Help
---

### Post by yrrej on 2008-09-11
Hi,

I just tried to install rapidsvn...After the installation
when I tried to run rapidsvn I get a "Seg Fault" on the
terminal screen and no other info...

I *can* use the command line version of svn but that is a
bit awkward.

Ldd shows that ldconfig can find all of the libraries that
rapidsvn uses, but perhaps I am missing a dependency of
a dependency...

Any suggestions on how to resolve the problem?

Is there another (free) gui svn client (that does not
require Java).

I am running ubuntu 8.0.4-1 in a Fusion VM on a 
MacBook Pro.

Thanks for any insights...

Jerry

---

### Post by yrrej on 2008-09-14
Hi,

I have not made any progress towards fixing "rapidsvn".

I took an older backup of my Ubuntu and updated the
rascal.

I then did an "apt-get install subversion" which completed
with no problems

I then did an "apt-get install rapidsvn" which completed
with no problems.

then I tried

gdb rapidsvn and got the following:

(no debugging symbols found)
BFD: /usr/lib/libwx_gtk2u_core-2.6.so.0: invalid string offset 37595719 >= 311624 for section `.dynstr'
BFD: /usr/lib/libwx_gtk2u_core-2.6.so.0: invalid string offset 70431744 >= 311624 for section `.dynstr'
(no debugging symbols found)
....
(no debugging symbols found)
[New Thread 0xb651a9c0 (LWP 6734)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread 0xb651a9c0 (LWP 6734)]
0xb7a1787c in ?? () from /usr/lib/libwx_gtk2u_core-2.6.so.0

________________________

What is the problem? Is anyone running rapidsvn?

Thanks for any insights...

Jerry

---

### Post by The Cog on 2008-09-14
I've been using rapidsvn for a couple of years or so without problems. So for at least 2 or 3 versions of Ubuntu, no problems. I always installed it from the repositories, and alwyas on 32-bit Ubuntu (never tried 64-bit).

That doesn't help much I know, except to confirm that it is not a problem that always happens. Makes me wonder if there's anything unusual with your setup.

---

### Post by yrrej on 2008-09-14
> **The Cog said:**
> I've been using rapidsvn for a couple of years or so without problems. So for at least 2 or 3 versions of Ubuntu, no problems. I always installed it from the repositories, and alwyas on 32-bit Ubuntu (never tried 64-bit).

That doesn't help much I know, except to confirm that it is not a problem that always happens. Makes me wonder if there's anything unusual with your setup.

I don't know what the problem is but a backtrace after the crash
gives:

(gdb) bt
#0  0xb7a4a87c in ?? () from /usr/lib/libwx_gtk2u_core-2.6.so.0
#1  0xb7bb13a5 in ?? () from /usr/lib/libwx_gtk2u_core-2.6.so.0
#2  0xb7a35900 in _init () from /usr/lib/libwx_gtk2u_core-2.6.so.0
#3  0xb7fcb9a0 in ?? () from /lib/ld-linux.so.2
#4  0xb7fcbad3 in ?? () from /lib/ld-linux.so.2
#5  0xb7fbe84f in ?? () from /lib/ld-linux.so.2

So it is bombing rather quickly....

Jerry

---

### Post by kosmiciatakuja on 2008-09-15
I have the same problem and as far as I could check this is related to incompatibility between RapidSVN and new subversion version 1.5. I also heard that some other subversion GUIs have similar problems after the update. Unfortunately I lack the coding abilities to patch RapidSVN so I'm waiting for the talented coders to fix it :)

---

### Post by kosmiciatakuja on 2008-09-15
Okay, a quick update: since I'm using Hardy, I have 0.9.4 version of RapidSVN, it seems there is a more recent 0.9.6 version out there. Maybe it is fixed already. Unfortunately Ubuntu has 0.9.6 version only for the upcoming Intrepid release. I tried to download the deb from Intrepid repositories but is says it has unsatisfiable dependencies (or something like that), which is to be expected since it's for a future release :(

If anybody knows how to install 0.9.6 (except compiling from sources of course) and can confirm this bug is fixed, please let us know. 

Thanks!

---

### Post by bkuhn on 2008-11-06
There is a bug filed for this in launchpad at [https://bugs.launchpad.net/ubuntu/+source/rapidsvn/+bug/270279](https://bugs.launchpad.net/ubuntu/+source/rapidsvn/+bug/270279)

---

### Post by baruch60610 on 2008-12-04
I'm using Hardy server edition, which of course doesn't have RapidSVN.  I still get segfaults, so probably it's the svn that's doing it, not RapidSVN.

---

### Post by Krijk on 2009-07-18
Does anybody have a permanent solution for this yet?

I run Hardy and installed Intrepid RapidSVN. It seems to work for me now (no problems yet), but obviously this is not the right way to do it.

---

