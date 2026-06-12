---
title: "JMicron JMB361 not working in 2..6.20-16 on MS-7235"
date: 2007-09-29
forum: Hardware &amp; Laptops
---

### Post by mux2000 on 2007-09-29
Hi,

I've seen lots and lots of discussion, lots of bug reports and claims that this has been solved numerous times, but no solution but buying expensive hardware. 
The problem:

Trying to mount the CD/DVD (connected to JMicron IDE) results in:

$ sudo mount /dvd
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

$  dmesg | tail
[ 5672.947545] eth1: no IPv6 routers present
[ 6443.694479] attempt to access beyond end of device
[ 6443.694484] sr0: rw=0, want=68, limit=4
[ 6443.694488] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 7318.343431] attempt to access beyond end of device
[ 7318.343436] sr0: rw=0, want=68, limit=4
[ 7318.343438] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16
[ 8221.883546] attempt to access beyond end of device
[ 8221.883551] sr0: rw=0, want=68, limit=4
[ 8221.883554] isofs_fill_super: bread failed, dev=sr0, iso_blknum=16, block=16

$ tail /etc/initramfs-tools/modules
libata
pata_jmicron
ata_piix
ahci
ata_generic
udf
isofs
ide-generic

USB mouse and keyboard support disabled. using ide-generic=1 and irqpoll boot options.

Linux mick 2.6.20-16-lowlatency #2 SMP PREEMPT Sun Sep 23 19:54:02 UTC 2007 i686 GNU/Linux

lshw and lspci outputs I will give on request.

Please... is there any hope for a fix on this or should I just switch distros? (a shame, I like Ubuntu)
Is there a fix in Gutsy Gibbon?

---

### Post by mux2000 on 2007-09-30
Replying to myself here, I've tried compiling the drovers for JMicron and ICH8 into the kernel, but  the result is a kernel that won't boot. The output looks like this:

Stating up...
JMB361: dma_base is invalid 
JMB361: dma_base is invalid 

Anyone else seen this before?

---

