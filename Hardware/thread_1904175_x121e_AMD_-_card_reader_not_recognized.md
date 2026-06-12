---
title: "x121e AMD - card reader not recognized"
date: 2012-01-04
forum: Hardware
---

### Post by krimskrams on 2012-01-04
Hi,

I have xubuntu 11.10 installed on my Leneovo x121e AMD based, 3051-5QG and everything works except the integrated card reader.

What wonders me is that it is not listed in lspci, comparing my output to [this one]("http://wiki.debian.org/InstallingDebianOn/Thinkpad/X121e-30515YG") the card reader device PCI 03:00.0 is missing.

I double checked my BIOS settings (card reader is enabled, upgraded to latest BIOS, factory reset of BIOS), tried with and without SD card inserted during boot, no change ... card reader is not detected.

Any clues? Or is it a hardware issue?

Bye, krimskrams

---

### Post by gordintoronto on 2012-01-04
What kernel version is in Xubuntu 11.10? You might try Googling 10ec:5209, which displays numerous bug reports.

---

### Post by krimskrams on 2012-01-04
Hi,

kernel is 3.0, output from uname -a
Linux miniorum 3.0.0-14-generic #23-Ubuntu SMP Mon Nov 21 20:28:43 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

What makes me a little "nervous" is the fact that neither lspci nor any other syslog shows the PCI ids for the card reader or any hint of an unknown device.

For example lspci -t shows bus 3 behind PCI bridge 7 however the device is missing:
lspci -t
-[0000:00]-+-00.0
           +-01.0
           +-01.1
           +-05.0-[01]----00.0
           +-06.0-[02]----00.0
           +-07.0-[03]--
           +-11.0
           +-12.0
           +-12.2
           +-13.0
           +-13.2
           +-14.0
           +-14.2
           +-14.3
           +-14.4-[04]--
           +-18.0
           +-18.1
           +-18.2
           +-18.3
           +-18.4
           +-18.5
           +-18.6
           \-18.7

One remark because of the Realtek r8192ce based wireless card I installed the backported 3.1 wireless drivers (package linux-backports-modules-cw-3.1-3.0.0-14-generic).

Bye, krimskrams

---

### Post by gordintoronto on 2012-01-04
Most card readers appear as USB devices, for example on my HP G62 laptop, from lsusb:
Bus 003 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader

It's possible Lenovo has switched to this approach. I had a 4 GB SDcard inserted when I captured that.

---

### Post by krimskrams on 2012-01-05
Hi,

I am pretty sure that the card reader is attached via PCI, have a look in the lspci output of exactly the same system in [Ubuntu bug 886779]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/886779"), look for device 03:00.0.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/886779](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/886779)

I will try to swap harddisks and install Windows see if the card reader is working under Windows.

Bye,
krimskrams

---

### Post by Mark Phelps on 2012-01-05
Laptops are infamous for using specialized hardware -- with specialized drivers.  Memory card readers seem especially prone to this.

Wish you luck, but you're unlikely to find a Linux driver for the memory card device.

I had the same problem and had to resort to using a USB-plugin memory card device -- which works because it's USB, not PCI.

---

### Post by krimskrams on 2012-01-20
Hi,

just to let you know: After installing Windows on my laptop the card reader was still not available.

I called Lenovo and send the laptop in for repair (fortunetaly still under warranty) and the mainboard was exchanged. Now the card reader is working fine again.

Bye,
krimskrams

---

