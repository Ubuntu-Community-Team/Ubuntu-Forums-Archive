---
title: "driver to compensate for broken hardware"
date: 2010-11-14
forum: Hardware
---

### Post by Debatablor on 2010-11-14
problem is - the headphone connection module as broken of the motherboard and now my build in speakers wont work.
the so called "9. headphone out" in following link- [http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML](http://h18000.www1.hp.com/products/quickspecs/11382_div/11382_div.HTML)

compaq - N662 or Evo N610c
driver page-
[http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=20&lc=en&cc=us&dlc=en&sw_lang=&product=316665#N1498](http://h10025.www1.hp.com/ewfrf/wc/softwareCategory?os=20&lc=en&cc=us&dlc=en&sw_lang=&product=316665#N1498)

more data?

00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio C
ontroller (rev 02)
        Subsystem: Compaq Computer Corporation Device 00b7
        Flags: bus master, medium devsel, latency 0, IRQ 11
        I/O ports at 4000 [size=256]
        I/O ports at 4400 [size=64]
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

that's what i got so far, not match.

so, what to do? should i hardwire the physical connection on the motherboard or look for a software solution?
at the moment i just have no sound.

---

### Post by Yellow Pasque on 2010-11-14
EDIT: Sorry, wrong thread.

---

### Post by Debatablor on 2010-11-16
please, help me. i only want to configure the driver to operate both headphone and speakers simultaneously or something like that


**** List of PLAYBACK Hardware Devices ****
card 0: I82801CAICH3 [Intel 82801CA-ICH3], device 0: Intel ICH [Intel 82801CA-ICH3]
Subdevices: 1/1 (- from this to -  0/1)
Subdevice #0: subdevice #0

---

### Post by Fafler on 2010-11-16
I'm not sure you can do that with hardware as old as yours. I can think of two other ways to fix it:

1. The headphone connector contains a small switch, that turns off the speakers when a plug is present. Solder a couple of short wires across the PCB from the input to the output terminals. To figure how to do it (if you cannot yourself), take apart the relevant part of the laptop and post a good picture of the PBM from both sides.

2. Buy a USB sound thingy from [eBay.]("http://cgi.ebay.com/USB-5-1-Audio-3D-Sound-Card-adaptor-Dell-Laptope-PC-/170549434858?pt=LH_DefaultDomain_0&hash=item27b589d9ea")

---

