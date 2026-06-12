---
title: "Compact flash/PCMCIA errors, Ricoh RL5c476 II"
date: 2006-06-12
forum: Hardware &amp; Laptops
---

### Post by DavidFong on 2006-06-12
My laptop, a Sharp CV-50 Muramasa, cannot handle compact flash cards, especially my 4GB compact flash card. It cannot consistently handle the partition, and ends up in a loop which tends to end in a crash.

I have both tried the default kernel (2.6.15) and a 2.6.16.20 modified kernel. I have tried the 'pollirq' option. My description on the problem is on my web-site (along with other Xubuntu 6.0.6 experiences) at [http://www.users.bigpond.com/vkelim/SuSE_notes/node95.html]("http://www.users.bigpond.com/vkelim/SuSE_notes/node95.html"),  unfortunately the node number will change frequently. I would happily put this information on the Laptop/Ubuntu Wiki, but despite creating an account I obviously have no idea how to change Wiki pages, or even how to login.

Some more detail follows...

In /var/log/message, it shows that /dev/hde and /dev/hde1 are identified. However, the messages go on to say that hdf is identified, which is totally spurious...
> 
Jun 11 19:21:25 localhost kernel: [4294862.728000] pccard: PCMCIA card inserted into slot 0
Jun 11 19:21:25 localhost kernel: [4294862.730000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
Jun 11 19:21:25 localhost kernel: [4294862.763000] pcmcia: registering new device pcmcia0.0
Jun 11 19:21:26 localhost kernel: [4294863.567000] hde: CF500, CFA DISK drive
Jun 11 19:21:26 localhost kernel: [4294863.722000] hdf: probing with STATUS(0x50) instead of ALTSTATUS(0x0a)
Jun 11 19:21:26 localhost kernel: [4294864.028000] hdf: ^L, ATA DISK drive
Jun 11 19:21:26 localhost kernel: [4294864.082000] ide2 at 0x100-0x107,0x10e on irq 11
Jun 11 19:21:26 localhost kernel: [4294864.088000] hde: max request size: 128KiB
Jun 11 19:21:26 localhost kernel: [4294864.089000] hde: 8060928 sectors (4127 MB) w/1KiB Cache, CHS=15744/16/32
Jun 11 19:21:26 localhost kernel: [4294864.089000] hde: cache flushes not supported
Jun 11 19:21:26 localhost kernel: [4294864.093000]  hde: hde1
Jun 11 19:21:26 localhost kernel: [4294864.108000] hdf: max request size: 1024KiB
Jun 11 19:21:27 localhost kernel: [4294864.305000] hdf: set_geometry_intr: status=0x91 { Busy }
Jun 11 19:21:27 localhost kernel: [4294864.305000] ide: failed opcode was: 0x27
Jun 11 19:21:27 localhost kernel: [4294864.307000] hdf: 864704322795998208
sectors (6755502521 MB) w/1536KiB Cache, CHS=65535/255/63
Jun 11 19:21:27 localhost kernel: [4294864.311000] hdf: cache flushes not supported
Jun 11 19:21:27 localhost kernel: [4294864.313000]  hdf:hdf: status error: status=0x91 { Busy }
Jun 11 19:21:27 localhost kernel: [4294864.338000] ide: failed opcode was: unknown
Jun 11 19:21:27 localhost kernel: [4294864.388000] ide2: reset: success
Jun 11 19:21:27 localhost kernel: [4294864.388000] hdf: status error: status=0x01 { Error }
Jun 11 19:21:27 localhost kernel: [4294864.388000] hdf: status error:
error=0x01 { AddrMarkNotFound }, LBAsect=1683644084225, high=100353, low=126977, sector=0

The above message came when the 'pollirq' option was used, and I was using kernel 2.6.15. The messages go on to say that the link is broken to hdf. Although /proc/partitions says that /dev/hde, or sometimes /dev/hde1, is present, they cannot be accessed.

Any assistance or ideas would be greatly appreciated! Or perhaps it is a kernel issue?

Cheerio, David.

---

### Post by DavidFong on 2006-06-13
Actually, is there a way to tell the kernel to avoid (and so not probe) a particular drive?

Like 'hdf=ignore'?

Cheerio, David.

---

