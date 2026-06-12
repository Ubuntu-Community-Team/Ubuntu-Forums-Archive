---
title: "Ubuntu Studio ALSA help"
date: 2008-11-21
forum: Hardware
---

### Post by dynobot on 2008-11-21
I have studio installed and am trying to use my ALSA supported soundcard Azuntech [sp].

I am going through the steps outlined on this page to configure ALSA [http://alsa.opensrc.org/Quick_Install]("http://alsa.opensrc.org/Quick_Install")

However at this step ./configure --with-sequencer=yes && make

I am getting this error
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for ranlib... ranlib
checking for a BSD-compatible install... /usr/bin/install -c
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for inline... inline
checking whether time.h and sys/time.h may both be included... yes
checking whether gcc needs -traditional... no
checking for current directory... /usr/src/alsa/alsa-driver-1.0.18a
checking cross compile... 
checking for directory with kernel source... ./configure: line 4773: cd: /usr/src/linux: No such file or directory
/usr/src/linux
checking for directory with kernel build... 
checking for kernel linux/version.h... no
The file /include/linux/version.h does not exist.
Please install the package with full kernel sources for your distribution
or use --with-kernel=dir option to specify another directory with kernel
sources (default is /usr/src/linux).


I installed version.h
ed@ubuntu:/usr/src/alsa/alsa-driver-1.0.18a/include$ ls
adriver.h            device_compat.h     mutex_compat.h
asm                  err_compat.h        old
autoconf-extra.h     firmware_compat.h   pci_ids_compat.h
autoconf-extra.h.in  hal2.h              pci_ids_compat.h.in
bitmap_compat.h      i2c-id_compat.h     platform_device_compat.h
compat_22.h          i2c-id_compat.h.in  pm_qos_params_compat.h
compat_64.h          isa_compat.h        ppc-prom-hack.h
compat_cs.h          kthread_compat.h    syscalls_26.h
config1.h            linux               uda1380.h
config1.h.in         Makefile            version.h
config.h             media               version.h.in
config.h.in          modules

But I still get the same error....

Please help...

---

### Post by dynobot on 2008-11-21
I think this issue should be an easy fix for the right person with the right knowledge.

I know I am close but not having done this before I have no idea which direction to go or what series of 2 or 3 commands I need to run.

If anyone has configured their ALSA for any sound card, please chime in as i am sure the procedure would be similar.

---

### Post by dynobot on 2008-11-22
After some trial and a lot of error it seems that OSS is the way to go but I have still not been able to make it work.

Anyone here use OSS to connect a their sound card???

---

### Post by dynobot on 2008-11-22
Come on, I know someone can help....

90% of everyone here listens to audio on their Linux machine so chances are most of you had to configure ALSA to work with your sound card.

You could at least point me in the right direction....

---

### Post by pelle.k on 2008-11-23
Make sure you've got all important stuff installed
```
sudo aptitude install build-essential libncurses-dev gettext xmlto xmltoman linux-headers-`uname -r`
```
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

Be sure to configure with
```
--with-moddir=/lib/modules/2.6.27-7-generic/kernel/ubuntu/misc
```
or something unless you want to move the modules manually later (i think anyway. it has been quite some time since i did this).

Also, if you're building modules only, remember to download the "driver" package and install with "make install-modules" instead of "make install".

Oh, and also, remember to update module cache with
```
depmod -a
```
When you've installed the modules.

---

### Post by bullethead on 2008-11-23
do this

in terminal "uname -a"

get the version of the linux kernel you're running from that

then "sudo apt-get install build-essentials"

then "sudo apt-get install linux-source-x.x.xx" where x is the version of the linux kernel you're running.

Then try that .configure step again, hopefully you'll be on your way.

---

### Post by dynobot on 2008-11-25
Thanks for your help but unfortunately I still have no sound.

The system can see my card and is not muted but nothing is coming out of coax.

---

### Post by pelle.k on 2008-11-25
Well, what card is it?

```
lspci | grep -i audio
```
install hwinfo, then
```
sudo hwinfo --sound
```
i think it is (check with hwinfo --help)
Also, what sound modules is loaded?
```
lsmod | grep -i snd
```

---

