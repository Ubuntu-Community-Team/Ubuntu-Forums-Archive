---
title: "DRDY error with IDE to SATA CD-ROM; after install?"
date: 2009-09-08
forum: Installation &amp; Upgrades
---

### Post by bgiannes on 2009-09-08
I have a new install (new build) the Mobo has three sata ports only. ZOTAC-ION-ITX 

My setup:
One sata 320Gb HD, and a IDE slim CD-ROM connected with a 'slim IDE to sata adaptor'.

The BIOS see's the CD-ROM and the HD just fine, i can select either to boot from with no problem.

However when the machine is booting to the HD into Ubuntu desktop 9.04 it reports a big list of DRDY ERROR's with Sata 2 (CD-ROM) and each time waits for a time out.  Boot takes +20 minutes.

Notes:
If i boot the PC w/o a CD or DVD in the drive the drive is unmount-able once ubuntu loads.

If i boot w/ a CD or DVD in the drive the drive is mount able but is very slow and/or doesn't read correctly.  DVD are unplayable.

The drives does work on an old IDE MoBo i have (the drive is not bad)

I was able to install the system without any problems or error, (from the install CD) only on the 1st boot did i see the DRDY errors.

If i unplug the 'slim IDE to sata adaptor' the system boots fast without error.


help please :confused:

---

### Post by presence1960 on 2009-09-08
The only time I have ever experienced those DRDY errors was in 8.04 and 8.10 when trying to come out of Suspend or Hiberbation, they would stream down the screen endlessly. I would have to to do a hard reboot. Maybe it has something to do with that adaptor you are using. When you boot it isn't connecting properly or communicating properly between the optical drive - connector - mobo sata port.

Suspend/Hibernate never worked for me in 8.04 & 8.10. I tried all the fixes I could find. Once I installed 9.04 it worked out of the box.

---

### Post by bgiannes on 2009-09-08
i'm not sure it's the adaptor as the system will boot to the CD-ROM w/o problem.  ie Live CD or Grub CD etc...

only when ubuntu is trying to load, (booting from HD) do i see the long list of DRDY errors.

could it be a problem with the kernel and the adaptor IDE to sata drivers?

---

### Post by presence1960 on 2009-09-08
> **bgiannes said:**
> i'm not sure it's the adaptor as the system will boot to the CD-ROM w/o problem.  ie Live CD or Grub CD etc...

only when ubuntu is trying to load, (booting from HD) do i see the long list of DRDY errors.

could it be a problem with the kernel and the adaptor IDE to sata drivers?

The problem has something to do with that adaptor whether it be the adaptor itself or drivers. You said the errors were SATA2 (CD-ROM)

---

### Post by bgiannes on 2009-09-08
> **presence1960 said:**
> The problem has something to do with that adaptor whether it be the adaptor itself or drivers. You said the errors were SATA2 (CD-ROM)


yes, SATA 2 (the port the CD-ROM is plug into).  

The HD is plug into SATA 1 and i've never had a problem with it.  I havn't tryed switching the plugs around, but did try pluging the CD-rom into sata port 3, and the system wouldn't boot, that shouldn't matter but it does??

---

### Post by bgiannes on 2009-10-02
the only solution was to replace the IDE ODD w/ a SATA ODD.


i think it's a kernel issue, that happens with older drives:confused:

---

### Post by dlowerre on 2010-01-08
I have EXACTLY the same problem as the original poster!  I bought a slim CD rom, which did not have a SATA connector.  I got an adapter (cheap from china!) and have the exact same result.

You know, I think I understand how it is and all but when it gets right down to it, it gets embarrassing when I am helping people convert to Linux and I keep having to advise them to buy newer hardware.

---

