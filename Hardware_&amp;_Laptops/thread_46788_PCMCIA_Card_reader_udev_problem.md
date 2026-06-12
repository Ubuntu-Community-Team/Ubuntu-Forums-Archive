---
title: "PCMCIA Card reader: udev problem?"
date: 2005-07-06
forum: Hardware &amp; Laptops
---

### Post by rtshome on 2005-07-06
I've a problem with my PCMCIA SD Card reader. The kernel seems to see the device correctly but i cannot find the /dev/hdx device in the dev directory.

Is there a udev problem not seeing the new disk?
This is the output of dmesg:

Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Probing IDE interface ide0...
hda: BN-SD Series, CFA DISK drive
ide0 at 0x100-0x107,0x10e on irq 3
ide-cs: hda: Vcc = 5.0, Vpp = 0.0

But ls -l /dev/hda:
ls: /dev/hda: No such file or directory

The /proc/ide listing is this:

aaa:~$ ls -lR /proc/ide/
/proc/ide/:
totale 1
-r--r--r--  1 root root 0 2005-07-06 11:26 drivers
lrwxrwxrwx  1 root root 8 2005-07-06 11:26 hda -> ide0/hda
dr-xr-xr-x  3 root root 0 2005-07-06 11:26 ide0

/proc/ide/ide0:
totale 0
-r--r--r--  1 root root 0 2005-07-06 11:26 channel
dr-xr-xr-x  2 root root 0 2005-07-06 11:26 hda
-r--r--r--  1 root root 0 2005-07-06 11:26 mate
-r--r--r--  1 root root 0 2005-07-06 11:26 model

/proc/ide/ide0/hda:
totale 0
-r--r--r--  1 root root 0 2005-07-06 11:26 driver
-r--------  1 root root 0 2005-07-06 11:26 identify
-r--r--r--  1 root root 0 2005-07-06 11:26 media
-r--r--r--  1 root root 0 2005-07-06 11:26 model
-rw-------  1 root root 0 2005-07-06 11:26 settings

Any idea?
Thank you in advance,
Denis

---

