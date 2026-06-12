---
title: "installproblems us robotics gigabit nic"
date: 2005-04-21
forum: Hardware &amp; Laptops
---

### Post by wza on 2005-04-21
i'm trying to upgrade our home lan by replacing 10/100 nics with gigabit nics from us robotics. i was hoping i would be able to do an easy install on two ubuntumachines but no such luck yet.

us robotics provide linuxdrivers; but the readme leads to nothing.

[http://www.usr-emea.com/support/s-p...e&prod=7902](http://www.usr-emea.com/support/s-p...e&prod=7902)

    quote:

    If you are running the target kernel, then you should be able to do :

    make clean modules (as root or with sudo)
    make install
    depmod -a



I'm not sure what 'running the target kernel' is, but my guess is I ain't doing so. Make clean modules returns:


    quote:
    make -C src/ clean
    make[1]: Entering directory `/mnt/jumbo/home/storage/r8169/src'
    rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
    make[1]: Leaving directory `/mnt/jumbo/home/storage/r8169/src'
    make -C src/ modules
    make[1]: Entering directory `/mnt/jumbo/home/storage/r8169/src'
    make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/mnt/jumbo/home/storage/r8169/src modules
    make: *** /lib/modules/2.6.10-5-386/build: Onbekend bestand of map. Stop.
    make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [modules] Fout 2
    make[1]: Leaving directory `/mnt/jumbo/home/storage/r8169/src'
    make: *** [modules] Fout 2
    root@debaser:/mnt/jumbo/home/storage/r8169 #



make install does the same trip.


Gotta say i'm totally noob in installing hardware on nix :(

tia

---

### Post by jdodson on 2005-04-21
> **wza]i'm trying to upgrade our home lan by replacing 10/100 nics with gigabit nics from us robotics. i was hoping i would be able to do an easy install on two ubuntumachines but no such luck yet.

us robotics provide linuxdrivers said:**
> http://www.usr-emea.com/support/s-p...e&prod=7902[/url]

    quote:

    If you are running the target kernel, then you should be able to do :

    make clean modules (as root or with sudo)
    make install
    depmod -a



I'm not sure what 'running the target kernel' is, but my guess is I ain't doing so. Make clean modules returns:


    quote:
    make -C src/ clean
    make[1]: Entering directory `/mnt/jumbo/home/storage/r8169/src'
    rm -f *.o *.ko *~ core* .dep* .*.d .*.cmd *.mod.c *.a *.s .*.flags
    make[1]: Leaving directory `/mnt/jumbo/home/storage/r8169/src'
    make -C src/ modules
    make[1]: Entering directory `/mnt/jumbo/home/storage/r8169/src'
    make -C /lib/modules/2.6.10-5-386/build SUBDIRS=/mnt/jumbo/home/storage/r8169/src modules
    make: *** /lib/modules/2.6.10-5-386/build: Onbekend bestand of map. Stop.
    make: Entering an unknown directorymake: Leaving an unknown directorymake[1]: *** [modules] Fout 2
    make[1]: Leaving directory `/mnt/jumbo/home/storage/r8169/src'
    make: *** [modules] Fout 2
    root@debaser:/mnt/jumbo/home/storage/r8169 #



make install does the same trip.


Gotta say i'm totally noob in installing hardware on nix :(

tia

right.  

have you installed "build-essential"?

you will need that to compile things.

you also need the "linux-headers" package to build against your kernel.

install those packages and try it again.  

oh and you need to do the install after you compile, as sudo or root.

---

