---
title: "boot attempts and fails to build Alsa after upgrading to 9.04"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by hjj on 2009-04-26
I need help with the following problem:

After upgrading from 8.10 to 9.04, on every boot there is an attempt to build Alsa which ends in error. The funny thing is that my sound works. I downloaded and installed alsa 1.0.19 but it doesn't help. When I reboot it spends several minutes trying to build alsa 1.0.18 again. I'm directed to the /var/run/alsa-driver.2327.log which shows these lines at the end: 

In file included from /usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_irq.c:3:
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c: In function 'pdacf_interrupt':
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c:48: error: implicit declaration of function 'get_irq_regs'
/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/../../alsa-kernel/pcmcia/pdaudiocf/pdaudiocf_irq.c:48: warning: comparison between pointer and integer
make[4]: *** [/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf/pdaudiocf_irq.o] Error 1
make[3]: *** [/usr/lib/alsa-driver-linuxant/pcmcia/pdaudiocf] Error 2
make[2]: *** [/usr/lib/alsa-driver-linuxant/pcmcia] Error 2
make[1]: *** [_module_/usr/lib/alsa-driver-linuxant] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [compile] Error 2

---

### Post by hjj on 2009-04-28
Solved! 

I just used the Synaptic Package Manager to install the following:

linux-backports-modules-2.6.28-11-server (2.6.28-11.12)
linux-backports-modules-jaunty-server (2.6.28.11.15)
linux-backports-modules-jaunty-virtual (2.6.28.11.15)
linux-image-2.6.28-11-server (2.6.28-11.42)

Now the system boots without a hitch.

---

### Post by OpenMercury on 2009-05-06
Synaptic won't allow installation of these packages.  It says that one of the packages is not available for download.

---

