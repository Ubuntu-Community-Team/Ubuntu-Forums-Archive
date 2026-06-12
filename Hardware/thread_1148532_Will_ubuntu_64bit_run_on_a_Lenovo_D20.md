---
title: "Will ubuntu 64bit run on a Lenovo D20?"
date: 2009-05-04
forum: Hardware
---

### Post by ecoxmit on 2009-05-04
A friend of mine is thinking of buying a Lenovo D20 workstation (a machine for heavy computational work). He asked Lenovo to install  Linux, and they told him they don't sell D20s with Linux (they do sell the D10s). So he asked me about whether Ubuntu will run on it. The configuration is:

2 Intel Xeon W5580 Processor (3.20GHz 1333MHz 8MB Turbo SMT) - 130W
24GB ECC DDR3 PC3-8500 SDRAM (2GBx12 UDIMMS)
ATI Fire Pro V3700 (256MB, DVI+DVI)
2 300GB SAS 3.5" Hard Drive - 15000 rpm

Anybody knows if Ubuntu will run fine here?

---

### Post by prgsdw on 2009-05-16
Bump as I'd like to know the same for the ThinkStation S20... These machines are very competitively priced IMHO. A nice unit with SAS drives on their outlet right now as a matter of fact...

---

### Post by slydog4 on 2009-06-27
Short answer: Nope.

Long answer:

The Marvell raid controller is not supported by the default ubuntu kernel.  There is a module for it (mvsas, I think), but the installation image will not detect any disks connected to it.  The second controller on the motherboard provides three sata ports for optical drives.  I am running a disk off that for the time being until I can work out the marvell.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352336](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/352336)

I also have a problem with my keyboard and mouse.  If I press and hold a key, I will get spurts of 1 to 4 repeats with several seconds of delay between.  Occassionally, there will be a spurt of 20 to 40 repeats, but not until I have waited for a while.  I get the same response from holding my left mouse button down.  e.g. Click and hold the scroll down widget in a browser window.  But I don't seem to have trouble dragging files, sliders, windows, etc.

Output is sometimes delayed in gnome-terminal and konsole.  It will look like nothing is happening until I press a key.  Then the window updates its display.  Xterm does not seem to be affected this way, but I may not have used it enough to see conclusively.

---

### Post by ecoxmit on 2009-06-27
thanks a lot for the reply!  

my friend went for a Dell with redhat instead.

---

### Post by wesleyyin on 2009-10-08
In fact, yes.

I loaded Ubuntu 9.04 on D20. The trick is to connect the hard-drive SATA cable to the ACHI SATA slots rather than the Marvell slots. The installation process is problem-free.

Once I get more time, I will study how to apply the 64-bit Linux driver of Marvell SAS at [http://www-307.ibm.com/pc/support/site.wss/MIGR-72070.html](http://www-307.ibm.com/pc/support/site.wss/MIGR-72070.html) .

---

### Post by Giou on 2009-10-12
Hello,

I am in a similar situation. I have a Lenovo ThinkStation D20 and I am trying to install Ubuntu.

I did what wesleyyin mentioned above, move the hard-drive to the ACHI slots from the Marvell ones, and the installation went on smoothly.

However, when I try to boot later, with the hard-drive connected to the ACHI slots, the system will not find any drives to boot from. Probably I need to configure the BIOS properly, but I am not sure what changes exactly I should make. I tried deactivating the Marvell driver from the BIOS, but it would still not find any drives.

Could anyone please help with the details? I am quite new to this system category, so I do not have much knowledge about such stuff. Thank you in advance!

---

### Post by wesleyyin on 2009-10-27
> **Giou said:**
> Hello,

I am in a similar situation. I have a Lenovo ThinkStation D20 and I am trying to install Ubuntu.

I did what wesleyyin mentioned above, move the hard-drive to the ACHI slots from the Marvell ones, and the installation went on smoothly.

However, when I try to boot later, with the hard-drive connected to the ACHI slots, the system will not find any drives to boot from. Probably I need to configure the BIOS properly, but I am not sure what changes exactly I should make. I tried deactivating the Marvell driver from the BIOS, but it would still not find any drives.

Could anyone please help with the details? I am quite new to this system category, so I do not have much knowledge about such stuff. Thank you in advance!

I guess you were right - some configuration in the BIOS to enable the ACHI/SATA ports is needed.

More good news . It is reported [here]("http://forums.lenovo.com/t5/Linux-Discussion/Linux-installation-problem-on-D20/m-p/127002") that **Ubuntu 9.10 supports Marvell SAS controller out of box**! It's just two days left for its final release.

---

