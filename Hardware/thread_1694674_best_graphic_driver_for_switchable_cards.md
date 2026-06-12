---
title: "best graphic driver for switchable cards"
date: 2011-02-24
forum: Hardware
---

### Post by merlin666 on 2011-02-24
I have a Lenovo T500 with switchable graphics:
lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Mobility Radeon HD 3650 [1002:9591]

After enabling FGLRX I had a blank screen but was able to recover, but now my screen looks terrible and I am not able to have visual effects etc. What is the best solution for graphics with such a set-up (10.04 right now).

---

### Post by Yellow Pasque on 2011-02-25
Make sure you completely purge fglrx: [http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Removing_the_Driver)

fglrx doesn't support hybrid/switchable graphics, so it's not going to work unless you have a way to disable the intel igp in the BIOS. The open-source ati and intel drivers that come installed are the only (accelerated) option to run both GPU's and switch between them.

---

