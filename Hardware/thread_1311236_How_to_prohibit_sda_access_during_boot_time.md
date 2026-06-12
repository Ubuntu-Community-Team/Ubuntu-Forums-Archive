---
title: "How to prohibit sda access during boot time"
date: 2009-11-02
forum: Hardware
---

### Post by ssiffzh on 2009-11-02
The internal hard disk of my laptop (SONY VAIO VGN-TZ50B) seemed corrupted, and I installed ubuntu 9.04&#12288;to a USB and use it to boot.
Since my hard disk went bad and I had no intention to exchange for a good one(I inquired SONY and it said that exchanging the hard disk itself would cost over 500 dollars) , I gave up and planed to use USB only. 
The problem is the BIOS still recognize the hard disk though it no longer worked. During my USB booting of Ubuntu, errors like the following keep printing on my console.

[ 65.154073] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[ 65.154076] res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[ 65.154236] ata1.00: status: { DRDY ERR }
[ 65.154289] ata1.00: error: { UNC }
[ 65.176842] ata1.00: configured for UDMA/100
[ 65.176859] ata1: EH complete
[ 70.868638] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
[ 70.868708] ata1.00: BMDMA stat 0x24
[ 70.868776] ata1.00: cmd 25/00:08:31:aa:18/00:00:14:00:00/e0 tag 0 dma 4096 in
[ 70.868780] res 51/40:05:34:aa:18/40:00:14:00:00/e0 Emask 0x9 (media error)
[ 70.868948] ata1.00: status: { DRDY ERR }
[ 70.869001] ata1.00: error: { UNC }
[ 70.892837] ata1.00: configured for UDMA/100
[ 70.892851] ata1: EH complete

After about 20 minutes, the Ubuntu started finally, though I can see that the sda error keeps outputing by using dmesg command.
First I thought disabling the internal hard disk would do the job, but there is no way to disable the hard disk in my BIOS (Phoenix TrustedCore).
I can not change the value of "Hard Disk Drive 0" in Advanced menu, all I can change is the system time and boot sequence.

And I also attempted a lot of option in Grub Kernel boot option such as noacpi, acpi=off, ide=no, ide0=noauto, noscsi, but nothing worked.

I want to know whether there is a way to configure the kernel never to access my internal hard disk (in my case sda)

Thanks a lot.

---

