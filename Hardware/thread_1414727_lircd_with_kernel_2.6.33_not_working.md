---
title: "lircd with kernel 2.6.33 not working"
date: 2010-02-23
forum: Hardware
---

### Post by rsm.gbg on 2010-02-23
Hi,

I've just setup my first Ubuntu mythtv box.
I'm sort of a Ubuntu newbie but I pretty good at Solaris :-)

Fact: a new HTPC with mythbuntu 9.10
HW: Intel DH55TC Mobo, i5 661 CPU, 4GB of RAM
Hauppauge HVR2200
Hauppage Remote control, the MCE version, TSHA-IR01, which is a TopSeed manufactured remote.

Due to bugs and all sorts of other issues I had to upgrade to a new kernel 2.6.33rc8
TV works, output to my Samsung 40" LCD TV works.
Sound is working, crappy stereo tv-sound but I hear what they say.

So far the only thing I can't get to work is the remote.
I tried all sorts of tricks from google searches so I wont list them all here, can't even remember what I've done.
My summary is this.
The remote is seen with 
roland@tvdator:~/Downloads/lirc-0.8.5pre2$ lsusb
Bus 001 Device 005: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 001 Device 004: ID 1784:0001 TopSeed Technology Corp. 
Bus 001 Device 003: ID 046d:08b2 Logitech, Inc. QuickCam Pro 4000
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
roland@tvdator:~/Downloads/lirc-0.8.5pre2$ 

I tried to reconfigure lirc:
roland@tvdator:/var/log$ sudo dpkg-reconfigure lirc
 * Stopping remote control daemon(s): LIRC                                                                                          [fail] 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service udev reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload udev
ls: cannot access /lib/modules/2.6.33-020633rc8-generic/kernel/ubuntu/lirc/: No such file or directory
 * Starting remote control daemon(s) : LIRC                                                                                         [ OK ] 
roland@tvdator:/var/log$
Seems like lirc can't install in the right kernel.

So the last straw was to recompile the source.
configure works OK, but make gives me this:
/lib/modules/2.6.33-020633rc8-generic/build/ SUBDIRS=/home/roland/Downloads/lirc-0.8.5pre2/drivers/lirc_dev modules \
        KBUILD_VERBOSE=1
make[4]: Entering directory `/usr/src/linux-headers-2.6.33-020633rc8-generic'
test -e include/generated/autoconf.h -a -e include/config/auto.conf || (        \
    echo;                                \
    echo "  ERROR: Kernel configuration is invalid.";        \
    echo "         include/generated/autoconf.h or include/config/auto.conf are missing.";\
    echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";    \
    echo;            

I'm feeling that I'm in deep water here, I don't want to destroy what is working.

Any advice how to continue?

---

### Post by zenyatta on 2010-02-27
See H-Online's kernel news ([here]("http://www.h-online.com/open/news/item/Kernel-Log-Coming-in-2-6-33-Part-5-Drivers-931993.html")):

> "The infrastructure for addressing infra-red receivers for remote controls has seen some major changes."

I don't know anything more specific but I'm sticking with 2.6.32 on my HTPC box for the time being...

---

### Post by rsm.gbg on 2010-02-27
> **zenyatta said:**
> See H-Online's kernel news ([here]("http://www.h-online.com/open/news/item/Kernel-Log-Coming-in-2-6-33-Part-5-Drivers-931993.html")):



I don't know anything more specific but I'm sticking with 2.6.32 on my HTPC box for the time being...

Is lirc included in the 2.6.32 kernel? if not could you "apt-get install lirc" and it worked?
The updated 2.6.31.20 has it.
Latest 2.6.33 first real release doesn't
lirc states support for 2.6.31

I read a bit more about 2.6.33 it seems that they try to merge ir-common and lircd.
I can't find any info on how to use/setup ir-common, is that a possible solution?

---

