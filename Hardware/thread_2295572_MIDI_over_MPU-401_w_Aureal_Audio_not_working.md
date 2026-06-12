---
title: "MIDI over MPU-401 w/ Aureal Audio not working"
date: 2015-09-19
forum: Hardware
---

### Post by henry-j-spare on 2015-09-19
I just installed an old Turtle Beach sound card with an Aureal au8830 chipset. Everything is fine and dandy, but I can't get Ardour (or anything) to find or use the MPU-401 interface. I only have a Kurzweil K2000 connected to it. (Stuck in the past, right?!)

 This is what I find when I run lshw:

 *-multimedia
                description: Multimedia audio controller
                product: Vortex 2
                vendor: Aureal Semiconductor
                physical id: 1
                bus info: pci@0000:03:01.0
                version: fe
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=snd_au8830 latency=32 maxlatency=12 mingnt=4
                resources: irq:22 memory:90000000-9003ffff ioport:1148(size=8) ioport:1140(size=8)

ALSAmixer shows the chipset as this:

Card: Aureal Vortex au8830
Chip: SigmaTel STAC9704

The keyboard works with an old Windows 2000 system with the same card. The following is my system specs:

Gateway GT5026E with a Pentium D 2.8GHz, running Ubuntu 15.04, 2GB RAM, plain old CD drive, ZIP250 drive, an Adaptec AHA-2940 for my SCSI junk, and a 250GB hard drive.

---

