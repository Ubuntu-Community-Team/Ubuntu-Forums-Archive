---
title: "Getting sound out of USB Audio Interface"
date: 2012-02-03
forum: Hardware
---

### Post by clruwe on 2012-02-03
[FONT=Verdana]Hello community, not sure if this is the right place to post this but, I'm having a hard time trying to get sound out of my external USB sound card. It does not show up in Preferences>Sound or in aplay -l. However, it does appear in lsusb.

The interface itself is called AKAI EIE Pro and it's USB 2. I don't need it to do anything but playback[/FONT].

Any help is highly appreciated!

C.

---

### Post by clruwe on 2012-02-03
[FONT=Verdana]Hello community, not sure if this is the right  place to post this but, I'm having a hard time trying to get sound out  of my external USB sound card. It does not show up in  Preferences>Sound or in aplay -l. However, it does appear in lsusb.
  
The interface itself is called AKAI EIE Pro and it's USB 2. I don't need it to do anything but playback[/FONT].

Any help is highly appreciated!

C.

---

### Post by jejeman on 2012-02-03
Give us output from
```
lsusb
```
```
aplay -l
```
```
sudo lshw -C multimedia
```
```
lsmod ] grep snd
```

---

### Post by wolfen69 on 2012-02-03
> **clruwe said:**
> However, it does appear in lsusb.
  


Post the output of lsusb. Also, you may have to disable the onboard sound in BIOS first.

---

### Post by lisati on 2012-02-03
Threads merged. Please do not start multiple threads for the same topic, it dilutes the community's efforts to help.

---

### Post by clruwe on 2012-02-03
> **lisati said:**
> Threads merged. Please do not start multiple threads for the same topic, it dilutes the community's efforts to help.
 
Sorry, wasn't sure where to post it. Below are the requested:

lsusb:

```
Bus 008 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 003: ID 0944:010f KORG, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c52b Logitech, Inc. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 010: ID 09e8:0010 AKAI  Professional M.I. Corp. 
Bus 002 Device 009: ID 2702:2702  
Bus 002 Device 008: ID 0944:010d KORG, Inc. 
Bus 002 Device 007: ID 088e:5036  
Bus 002 Device 006: ID 0819:0101  
Bus 002 Device 004: ID 0409:005a NEC Corp. HighSpeed Hub
Bus 002 Device 003: ID 1a40:0101 TERMINUS TECHNOLOGY INC. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```aplay -l

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```sudo lshw -C multimedia

 ```
*-multimedia UNCLAIMED  
       description: Audio device
       product: nVidia Corporation
       vendor: nVidia Corporation
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: a1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:fbbfc000-fbbfffff
  *-multimedia
       description: Audio device
       product: 82801JI (ICH10 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:f9ff8000-f9ffbfff
```lsmod ] grep snd

```
Usage: lsmod
```Hope that's correct and thank you very much for your help!

---

### Post by clruwe on 2012-02-05
It would appear I received more replies in the Ubuntu Studio section, where I received replies in a matter of hours. Haven't heard from anyone all weekend since the post was moved here... Is this definitely the right place for it? Anyone?

Many thanks!

---

### Post by MIJ-VI on 2012-08-27
*bump* for more info.

---

