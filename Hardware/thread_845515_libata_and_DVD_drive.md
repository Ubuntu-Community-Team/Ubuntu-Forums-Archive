---
title: "libata and DVD drive"
date: 2008-06-30
forum: Hardware
---

### Post by PoisonIvy on 2008-06-30
Hi,

Could anyone please advise on how to get a DVD player to work better in Hardy (all updates applied, so this is the 2.6.24-19-generic kernel)? Judging from trawling the user groups it looks like libata might be the problem. The machine has an ASUS A8V deluxe motherboard with an x2 4200 processor running in 32 bit mode. The motherboard has two hard drive chips, the VIA chipset and a Promise chipset. The DVD drive is connected to the VIA chipset. There is also a RAID 1 SATA configuration from the VIA chipset and a regular IDE drive. The Promise chipset has an SATA drive on it.

The symptom can be seen from the dmesg log:

[ 4857.663117] ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4857.663130] ata6.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 4857.663132]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 4857.663133]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 4857.663137] ata6.01: status: { DRDY }
[ 4857.663157] ata6: soft resetting link
[ 4858.373957] ata6.01: configured for UDMA/33
[ 4858.373973] ata6: EH complete
[ 4868.354683] ata6.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 4868.354695] ata6.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
[ 4868.354697]          cdb 1e 00 00 00 01 00 00 00  00 00 00 00 00 00 00 00
[ 4868.354699]          res 40/00:02:00:08:00/00:00:00:00:00/b0 Emask 0x4 (timeout)
[ 4868.354703] ata6.01: status: { DRDY }
[ 4868.354722] ata6: soft resetting link
[ 4869.065527] ata6.01: configured for UDMA/33
[ 4869.065544] ata6: EH complete

This repeats until the DVD goes to PIO mode.

Some suggestions have been tried:
- Replaced DVD drive from Samsung to LiteOn
- Replaced cable
- Tried a second IDE card plugged into PCI slot
- It all seems to work fine under Windows 2000 (not sure whether this is saying very much.

None of the above made any difference. I've tried putting combined_mode=libata on the kernel boot line, but, this has not made any difference.

The final thing left to try is libata.dma=1 which should switch dma mode off for DVD. However, I can't figure out how to do this. I've tried putting it on the kernel command line, but, Ubuntu says unrecognised option. I've tried putting 
   options libata dma=1 
into 
   /etc/modprobe.d/options. 
However, doing a 
  cat /sys/module/libata/parameters/dma
still returns
  7
Which should suggest that /etc/modprobe.d/options has not been read. I did try and run initramfs, but, this has put my out of my depth as the machine hung on boot up.

Could anyone suggest anything else, or some other diagnosis?

Thank you for taking the time to read this post.

Richard

---

### Post by jb23 on 2008-07-31
Hello,

have you found a solution?

If you want that "options libata dma=1" take effect then you have to rebuild the initrd file 

> 
$ sudo cp /boot/initrd.img-`uname -r` /boot/initrd.img-`uname -r`.bak
$ sudo mkinitramfs -o /boot/initrd.img-$( uname -r )


I've tried that but the error message still remain while cat /sys/module/libata/parameters/dma returns 1.

same like this one.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/231575)

I hope that Alan Cox fix that dma problem soon.

---

### Post by PoisonIvy on 2008-09-30
Hi jb23,

Thanks for your post on how to use mkinitramfs. This worked and the machine did reboot. With this it was possible to change whether drive was connecting over DMA. The downside is not connecting over DMA it seems to choppy to watch a DVD.

Cheers,
Richard

---

