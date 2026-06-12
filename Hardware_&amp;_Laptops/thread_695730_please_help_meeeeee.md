---
title: "please help meeeeee"
date: 2008-02-13
forum: Hardware &amp; Laptops
---

### Post by harivadakara on 2008-02-13
i installed ubuntu7.10 in my hp520 but no sound.my audio details is given below
       description: Audio device
       product: 82801G (ICH7 Family) High Definition Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
ANY ONE KNOWS HOW TO FIX THIS PROBLEM

---

### Post by jan quark on 2008-02-13
please the next time use a more descriptive title than just pls help me
thank you

---

### Post by PurposeOfReason on 2008-02-13
You're going to edit the /etc/modprobe.conf file to have something like

options snd-hda-intel model=_______

Google around about it or wait, I'll too look around for what model to use with that hp.

---

