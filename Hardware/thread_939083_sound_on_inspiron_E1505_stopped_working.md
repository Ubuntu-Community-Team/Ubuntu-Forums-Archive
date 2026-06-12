---
title: "sound on inspiron E1505 stopped working"
date: 2008-10-05
forum: Hardware
---

### Post by shortridge11 on 2008-10-05
I'm running ubuntu 8.04 and all audio on my inspiron E1505 dell laptop has stopped working.  It has worked fine for about a year, and today it stopped working.  Also, when i try to do a restart, it freezes and i have to do a manual power cycle by holding the power button.  These two problems may or may not be related, but they started around the same time, so there may be a connection.  I'm not sure how to get find the name of my sound card.  The hardware testing program on System-Administration-Hardware Testing just calls it Intel, and it's an integrated sound card.

in terminal- sudo lshw gives this snippet about my audio

*-multimedia
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


on a side note- how do you make the little code boxes in posts? It would clean up my posts a little more.

Any help is appreciated.

---

