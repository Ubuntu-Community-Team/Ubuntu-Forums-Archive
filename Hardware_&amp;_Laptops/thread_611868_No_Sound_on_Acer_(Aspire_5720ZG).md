---
title: "No Sound on Acer (Aspire 5720ZG)"
date: 2007-11-13
forum: Hardware &amp; Laptops
---

### Post by Fred_S on 2007-11-13
Just bought a new laptop, Acer Aspire 5720ZG.

Sysinfo on my Soundcard:
Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
Subsystem: Acer Incorporated [ALI] Unknown device 011e

I'm currectly using Ubuntu Gutsy Gibbon (7.10).
Everything seems to work like it should except the sound. 
There are completely no sound on headphone, or speakers. i've tried to do something in alsamixer. Seems that it still runs some sound drivers, i can turn the volume on the side key of the computer (turning it high and low) and even mute.

---

### Post by Fred_S on 2007-11-14
Have been through some of my friends advices but still nothing yet, if you need any other info just tell me.

---

### Post by smyrman on 2007-12-27
Follow this link, and scroll to method E:

[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller")

I used this method on Acer Aspire 5720ZG and confirms that it works=)

EDIT:
Here is a extract from method E:
    *use this already pacthed,ready to install, [linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb]("http://c.chez.fred.free.fr/linux-ubuntu-modules-2.6.22-14-generic_2.6.22-14.37.1_i386.deb").
      Note: It only works with an up-to-date Gutsy.
    *

      Add the following line in [B]/etc/modprobe.d/alsa-base:
[/B]
    **  options snd-hda-intel model=acer**

      Note: You can specify one of the following model : acer, toshiba, 3stack or auto Note 2: For MSI PR200, use model=targa-dig
    *

      Reboot

---

### Post by Yellow Pasque on 2007-12-27
Failing the above, try OSSv4 (link in sig) if you're still looking for a solution to no sound problem.

---

