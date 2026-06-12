---
title: "DVD Burning with Philips SDVD8441 doesn't work"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by smolko on 2008-01-18
Hello, I need some help with my CD/DVD drive Philips SDVD8441.

It simply refuses to burn in Ubuntu, with a strange error (better said, no real error is displayed, I've attached the debugging output from K3B), however everything works fine in Slax. The difference is, that Slax recognizes the drive as ATAPI device and lists it under /dev/hda. As you can see in the following output from lshw, it's recognized as an SCSI device in Ubuntu:

```
  *-cdrom                 
       description: DVD writer
       product: DVD+-RW SDVD8441
       vendor: PHILIPS
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: PV32
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 status=ready
     *-disc
          physical id: 0
          logical name: /dev/cdrom

```

Could this be some HAL or kernel module issue?

Thank you for you suggestions.

---

### Post by jeffus_il on 2008-01-18
It seems to find the device and access it OK,  so I think that's not a problem, my drive is also recognized as a scd and it works fine.
Did you use K3B in Slax?
It fails while doing an internal dd, a raw copy from disk to the DVD.
You could try cdrecord from the command line and see how it responds.
or even a regular ```
dd if=my.iso of=/dev/scd0
```

I just noticed that in the K3B settings under "programs" that I have all the programs installed that are listed in the box, I may not be using the internal dd but cdrecord, for instance, have a look there.

---

