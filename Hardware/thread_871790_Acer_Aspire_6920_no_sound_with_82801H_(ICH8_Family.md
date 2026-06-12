---
title: "Acer Aspire 6920 no sound with 82801H (ICH8 Family) HD Audio Controller"
date: 2008-07-27
forum: Hardware
---

### Post by tomprider on 2008-07-27
Hi happy ubuntu users:)

I have got ACER aspire 6920 with 82801H (ICH8 Family) HD Audio Controller and i don't hear any sound...

My device: 

tomprider@tomprider-laptop:~$ sudo lshw -C multimedia
  *-multimedia            
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

and

tomprider@tomprider-laptop:~$ sudo apt-get install linux-backports-modules
I'am reading lists of packages... Done
Vytvá&#345;ím strom závislostí       
Reading status actions... Done
E: I can't find package linux-backports-modules
tomprider@tomprider-laptop:~$ 

Can you help me please?????

---

### Post by triple.eh on 2008-07-27
I have the same laptop and have not had success using ALSA drivers.

However, I am now using OSS with decent results.

Here's a link to the bug and solution:  [https://bugs.launchpad.net/ubuntu/+bug/218165/comments/17](https://bugs.launchpad.net/ubuntu/+bug/218165/comments/17).

---

