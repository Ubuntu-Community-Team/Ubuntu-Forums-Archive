---
title: "No sound after upgrade 8.04 -&gt; 8.10"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by btwong10 on 2009-03-26
I recently upgraded from 8.04 to 8.10 and have since lost my sound.

I new it had something to do with my ALSA drivers, so i followed this guide to help me upgrade my drivers:

[http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/]("http://monespaceperso.org/blog-en/2009/02/10/acer-aspire-6920-no-sound-on-ubuntu-810-upgrade-of-alsa/")

*note: my laptop is a Asus m51sn, but i followed these instructions before for the 8.04 setup, and it worked perfectly.

Anyway, once i followed all these steps, i checked my driver versions using:
> cat /proc/asound/version
and what was returned was:
> Advanced Linux Sound Architecture Driver Version 1.0.16.
Compiled on Jun 18 2008 for kernel 2.6.24-19-generic (SMP).

why are my driver still an old version???

i then did a:
> aptitude search linux-headers
and the return was:
> v   linux-headers                                           -
v   linux-headers-2.6                                       -
i A linux-headers-2.6.27-11                                 - Header files related to Linux kernel version 2.6.27
i A linux-headers-2.6.27-11-generic                         - Linux kernel headers for version 2.6.27 on x86/x86_64
p   linux-headers-2.6.27-11-server                          - Linux kernel headers for version 2.6.27 on x86/x86_64
p   linux-headers-2.6.27-3-rt                               - Linux kernel headers for version 2.6.27 on Ingo Molnar's full rea
p   linux-headers-2.6.27-7                                  - Header files related to Linux kernel version 2.6.27
p   linux-headers-2.6.27-7-generic                          - Linux kernel headers for version 2.6.27 on x86/x86_64
p   linux-headers-2.6.27-7-server                           - Linux kernel headers for version 2.6.27 on x86/x86_64
p   linux-headers-2.6.27-9                                  - Header files related to Linux kernel version 2.6.27
p   linux-headers-2.6.27-9-generic                          - Linux kernel headers for version 2.6.27 on x86/x86_64
p   linux-headers-2.6.27-9-server                           - Linux kernel headers for version 2.6.27 on x86/x86_64
i   linux-headers-generic                                   - Generic Linux kernel headers
v   linux-headers-lbm                                       -
v   linux-headers-lbm-2.6                                   -
p   linux-headers-lbm-2.6.27-11-generic                     - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-lbm-2.6.27-11-server                      - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-lbm-2.6.27-7-generic                      - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-lbm-2.6.27-7-server                       - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-lbm-2.6.27-9-generic                      - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-lbm-2.6.27-9-server                       - Header files related to linux-backports-modules version 2.6.27
p   linux-headers-rt                                        - Rt Linux kernel headers
p   linux-headers-server                                    - Linux kernel headers on Server Equipment.
p   linux-headers-virtual                                   - Linux kernel headers for virtual machines

this all looks like a new kernal to me, but for the life of me my sound wont work. I have even changed all the sound settings to use ALSA, but nothing happens.

What else is strange is that i start up amarok, the music plays no problems, but just no sound.

can someone please help me.

thanks in advance

---

### Post by PhoenixP3K on 2009-03-30
I don't think the loss of sound was caused by your upgrade to 8.10
I have an Asus Aspire 5610 and I've been using 8.10 with it, sound was working fine until kernel 2.6.27-11 came in. To have sound back. I had to rollback to kernel 2.6.27-9

---

### Post by PhoenixP3K on 2009-03-30
Sorry to double post. But this other post I made might be the solution you need. Check what sound card you have with "aplay -l"

[http://ubuntuforums.org/showthread.php?p=6984016#post6984016](http://ubuntuforums.org/showthread.php?p=6984016#post6984016)

---

### Post by btwong10 on 2009-04-04
> **PhoenixP3K said:**
> Sorry to double post. But this other post I made might be the solution you need. Check what sound card you have with "aplay -l"

[http://ubuntuforums.org/showthread.php?p=6984016#post6984016](http://ubuntuforums.org/showthread.php?p=6984016#post6984016)

i have the following:

> card 0: Intel [HDA Intel], device 0: ALC861VD Analog [ALC861VD Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

i think i need tor esearch more on this. its killing me!!

i am that close to re-installing everything.

---

