---
title: "Highpoint RocketRAID 2680"
date: 2009-09-10
forum: Installation &amp; Upgrades
---

### Post by tgrimley on 2009-09-10
I recently bought a [Highpoint RocketRAID 2680]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115057") to migrate my mdadm raid5 off my very much saturated PCI bus.

I am running 32bit 8.04LTS on an opteron.  I am having trouble installing the drivers.

Problems:
P1) provided kernel modules are for 2.6.24-16. I am running 2.6.24-24,  as it is the latest (and -16 isn't even in apt anymore as far as I can tell..)
S1) tried to change the file names so they would insert it, kernel wasn't having it.. okay.

P2) downloaded source, compiled, inserted into initrd; modprobe rr2680, drives show up.  I do a quick hdparm -tT bench, and yes finally things are not saturated, yes!!! 220MB/s read on a 3 disk raid5, not too shabby so f... oh, kernel panic
S2) tried different kernels: -386, -server, -generic, previous version... did memtest for 12 hours, no problems.

I get a 'kernel panic interrupt handler not syncing' type panic. 

not sure what to try next, any suggestions? anyone have this card working successfully??

---

### Post by tgrimley on 2009-09-11
Flashed the bios up to v1.1 (latest) and recompiled the drivers.  System will boot fine with the card but no drives.  Seems to be related to accessing the drives.. any help please?!

---

### Post by tgrimley on 2009-09-15
bump, no help at all?

---

### Post by babeliak on 2009-09-16
I can't help with kernel issues :confused:

---

### Post by tgrimley on 2009-09-16
Unfair!

Anyway, I got it to work under 9.04 64 bit... sorta.  According to highpoint support, which finaaallly got back to me, it doesnt support the hdparm or hddtemp commands, so I get kernel panics when I try them.. or set up munin.. or do anything else which tries to run them!  Also, they say smartmontools should be okay, but they aren't and I'm getting kernel panics still.  I'll post if HP support gets back to me WHY it doesn't support hdparm, etc.

---

### Post by okivash on 2009-09-20
> **tgrimley said:**
> I recently bought a [Highpoint RocketRAID 2680]("http://www.newegg.com/Product/Product.aspx?Item=N82E16816115057") to migrate my mdadm raid5 off my very much saturated PCI bus.

I am running 32bit 8.04LTS on an opteron.  I am having trouble installing the drivers.

Problems:
P1) provided kernel modules are for 2.6.24-16. I am running 2.6.24-24,  as it is the latest (and -16 isn't even in apt anymore as far as I can tell..)
S1) tried to change the file names so they would insert it, kernel wasn't having it.. okay.

P2) downloaded source, compiled, inserted into initrd; modprobe rr2680, drives show up.  I do a quick hdparm -tT bench, and yes finally things are not saturated, yes!!! 220MB/s read on a 3 disk raid5, not too shabby so f... oh, kernel panic
S2) tried different kernels: -386, -server, -generic, previous version... did memtest for 12 hours, no problems.

I get a 'kernel panic interrupt handler not syncing' type panic. 

not sure what to try next, any suggestions? anyone have this card working successfully??

I recently bought 2 of these cards as well as Im in the process of building a storage server and ran into the exact same problems... as the only precompiled Ubuntu x86-64 driver was for kernel-2.6.24-16 and the download for Ubuntu Server 8.04LTS is running kernel-2.6.24-24, I was stuck from the start having to pull source and compile my own drivers for install. I actually found an original verion of Ubuntu Server 8.04LTS running the original kernel and installed with that and the Highpoint provided driver, this installed smoothly and runs stable. I downloaded source yesterday for 2.6.24-24-x86-64 and compiled a newer driver, but upon UbuntuServer 8.04.3 install, the newly compiled driver wouldnt work for me so it never would see the drives. Anybody have a download link for a pre-compiled 64-bit driver on the 2.6.24-24 kernel(current version of UbuntuServer 8.04.3 LTS)?:)

Regards, Tony

---

### Post by okivash on 2009-09-20
Heres a link to the download file for the rr2680 driver source....

[http://www.support-highpoint-tech.com/Main/rr26xx/268x/Linux/opensrc/rr268x-linux-src-v1.1-090407-1336.tar.gz](http://www.support-highpoint-tech.com/Main/rr26xx/268x/Linux/opensrc/rr268x-linux-src-v1.1-090407-1336.tar.gz)

 If anyone who happens to be running Ubuntu8.04.3 LTS Server 64-bit-AMD version with kernel 2.6.24-24, and could spare a few minutes to compile the driver and send a link to it....  it sure would be greatly appreciated!

---

### Post by tgrimley on 2009-09-21
I managed to get this driver compiled and installed under 9.04 x64 and figured out the kernel panics later were from using munin which polls the drives with hddtemp (which according to highpoint support is mysteriously unsupported).

Also hdparm, hddtemp, and smartctl will cause a kernel panic.  Awesome. :D  Other than that it's stable and reasonably fast.

---

### Post by okivash on 2009-09-21
> **tgrimley said:**
> I managed to get this driver compiled and installed under 9.04 x64 and figured out the kernel panics later were from using munin which polls the drives with hddtemp (which according to highpoint support is mysteriously unsupported).

Also hdparm, hddtemp, and smartctl will cause a kernel panic.  Awesome. :D  Other than that it's stable and reasonably fast.


This is good to know... thanks for the info!

---

### Post by geppz on 2010-05-04
Could this be a bug similar to this?
[https://bugzilla.kernel.org/show_bug.cgi?id=14831](https://bugzilla.kernel.org/show_bug.cgi?id=14831)
and maybe also the fix could be similar?
[http://lkml.org/lkml/2010/4/26/335](http://lkml.org/lkml/2010/4/26/335)

---

### Post by macrillo on 2011-11-05
Works fine under Natty with this guide: [https://help.ubuntu.com/community/RocketRaid]("https://help.ubuntu.com/community/RocketRaid")

I've put together patches for v1.4 and v1.6 drivers and they compile successfully against 2.6.35 (Maverick), 2.6.38 (Natty) and 3.0.0 (Oneiric) -kernels, i'm using 2.6.38-12-server at the moment.

If someone wants to test, they can be found at: [http://www.macronet.fi/dev/rr268x/]("http://www.macronet.fi/dev/rr268x/")

---

