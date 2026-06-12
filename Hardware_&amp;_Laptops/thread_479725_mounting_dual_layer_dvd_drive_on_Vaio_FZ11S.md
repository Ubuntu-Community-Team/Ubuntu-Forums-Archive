---
title: "mounting dual layer dvd drive on Vaio FZ11S?"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by jpb39 on 2007-06-20
My laptop has a dual-layer DVD drive, which the BIOS recognizes and I can boot from. When I boot into 7.04, the system tries to automount it and produces a zombie volume /cd-rom 1. When I attempt to access the volume it reports: 'Unable to mount the selected volume, special device /dev/hda does not exist'. So clearly the default entry in fstab is wrong. But it is unclear to me how to find the drive (or even determine whether there is a driver for it in the amd64 distribution).

Thanks in advance for any hunting strategies,

 JPB

---

### Post by kiloxxx on 2007-07-19
I have a Vaio Fz11z that comes with a bluray double layer DVD and - I think - with the same problem. At the moment only this expedient worked for me:

> I have this problem also. Can work it around in this way:
- Open a terminal
- write
sudo modprobe -v ide-generic

you should get /dev/hd(a-b-c-d) (primary/secondary master/slave), /dev/cdrom, /dev/cdrw, /dev/dvd, /dev/dvdrw depending on your configuration. The drive should also be visible in computer:/// and inserted discs should be automounted.

- If it worked, write in the terminal
sudo gedit /etc/modules

- add this line in it and save
ide-generic

Modifying /etc/fstab accordingly might be needed.
Please notice that ide-generic doesn't give you any DMA mode (and this is bad). This is just a temporary workaround, I think something should be fixed in the kernel...

I hope it can help.

---

