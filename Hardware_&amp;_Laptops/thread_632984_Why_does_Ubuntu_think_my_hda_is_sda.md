---
title: "Why does Ubuntu think my hda is sda?"
date: 2007-12-06
forum: Hardware &amp; Laptops
---

### Post by newnet on 2007-12-06
While installing Ubuntu, it reads my hard drive as sda as opposed to hda.  Why does it think it is a SCSI or some other special device?

---

### Post by mozetti on 2007-12-06
SATA hard drives are listed as sda. Does the hard drive in your laptop connect using SATA?

---

### Post by info2 on 2007-12-06
As far as I remember this is because Ubuntu (and oder Distributions) is using a new generic driver to access drives. This driver can handly PATA as well as SATA drives and it shows up all your drives as a "sdX". No need to worry about it.

---

### Post by newnet on 2007-12-06
I am not using SATA, but rather IDE (PATA).

It is rather annoying trying to remember my hda as sda.  Because when I try to mount a special device, I forget that my hda is now mistaken as sda by Ubuntu.

---

### Post by the100thmonkey on 2007-12-06
It's been that way since Feisty. 

All drives are listed under the same naming convention now - SDA, SDB, SDC, regardless of whether they're P-ATA or S-ATA

---

### Post by Zylar on 2007-12-13
Are there exceptions?  

I'm looking right now at 2 ubuntu 7.10 servers, both with a single IDE HD, both installed from the same CD.  One says it's hda, the other sda.  Very different h/w in both, but the older of the 2 is the sda one.  Is it based on controller chipset?

Edit:

Nevermind, looks to be driver/chipset related.  Has to do with some changes back around Fiesty in the kernel, moving some (eventually all?) ide drivers into a new ATA library that does both sata/ide.

---

