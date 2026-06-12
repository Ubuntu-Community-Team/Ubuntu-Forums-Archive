---
title: "CD won´t automount, but DVD will"
date: 2007-10-11
forum: Hardware &amp; Laptops
---

### Post by mikeczap on 2007-10-11
First:  the HW & OS particulars:

I´ve got an old Presario 1250, with an AMD K6 CPU and 128meg of RAM.  I loaded it with the
Feisty Fawn 7.04 alternative install disk, no problem.  After some tweaking, I´m really
liking this older laptop for Ubuntu, except that it will only occasionally recognize CD´s
(Data or Audio) and mount them.  It will reliably automount DVD´s, however.

I haven´t monkeyed with the devices or /etc/fstab, as I´m a Linux newbie (despite
a fair amount of rusty SVR4 experience), and I´m sure that the HW is functioning
properly.

I did capture the following section of /var/log/dmesg, however:

[   11.880000]     ide1: BM-DMA at 0x1828-0x182f, BIOS settings: hdc:DMA, hdd:pio
[   13.836000] hdc: TOSHIBA DVD-ROM SD-C2402, ATAPI CD/DVD-ROM drive
[   14.668000] hdc: ATAPI 24X DVD-ROM drive, 128kB Cache, UDMA(33)

The device is on /dev/hdc (which looks pretty normal), but I am confused by it
showing up as two devices during boot.

Interestingly, this is what happens when I try to mount from the command line:

>:~$ sudo mount -t iso9660 /dev/hdc /media/cdrom0
mount: No medium found

The discs in question are home burned, but are readable on Windows machines
and even, intermittantly, on the machine itself.

What am I missing?

Mike Czaplinski

---

