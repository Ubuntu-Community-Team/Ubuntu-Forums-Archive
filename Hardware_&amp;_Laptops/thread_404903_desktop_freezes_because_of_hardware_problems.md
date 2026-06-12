---
title: "desktop freezes because of hardware problems"
date: 2007-04-09
forum: Hardware &amp; Laptops
---

### Post by A-1337 on 2007-04-09
Hello!
I have ubuntu edgy 6.10 and it begin to freeze from time to time. Any keys do no effect except for reset key.

I've examined /var/log/messages and found following right before freeze:
```

Apr  9 07:57:21 dmitry-dsk-ubuntu kernel: [17180429.040000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:57:21 dmitry-dsk-ubuntu kernel: [17180429.040000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:57:21 dmitry-dsk-ubuntu kernel: [17180429.040000] ide: failed opcode was: unknown
Apr  9 07:57:43 dmitry-dsk-ubuntu kernel: [17180450.808000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:57:43 dmitry-dsk-ubuntu kernel: [17180450.808000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:57:43 dmitry-dsk-ubuntu kernel: [17180450.808000] ide: failed opcode was: unknown
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180457.944000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180457.944000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180457.944000] ide: failed opcode was: unknown
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180458.428000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180458.428000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:57:50 dmitry-dsk-ubuntu kernel: [17180458.428000] ide: failed opcode was: unknown
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.716000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.716000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.716000] ide: failed opcode was: unknown
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.784000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.784000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:58:01 dmitry-dsk-ubuntu kernel: [17180468.784000] ide: failed opcode was: unknown
Apr  9 07:58:12 dmitry-dsk-ubuntu kernel: [17180480.088000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Apr  9 07:58:12 dmitry-dsk-ubuntu kernel: [17180480.088000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }
Apr  9 07:58:12 dmitry-dsk-ubuntu kernel: [17180480.088000] ide: failed opcode was: unknown
Apr  9 07:59:49 dmitry-dsk-ubuntu syslogd 1.4.1#18ubuntu6: restart.

```

Does it mean my hda device is garbage now? Advice me what to do next.

---

### Post by kvonb on 2007-04-09
It certainly doesn't look good!

First copy anyhing you need from the drive if you can, boot from the LiveCD for that.

It might not be the drive, I had the exact same errors a few months ago on my server, it was a faulty mainboard.  Check the mainboard for blown capacitors, they will look different to the others on the mainboard, they will have a rounded top.

If you have some that are blown, you can replace them or buy a new mainboard!

Next check the hard drive for bad sectors, you can use fsck from the LiveCD.

Regards, Kev :)

---

### Post by frodon on 2007-04-17
Could you also tell us the motherboard you are using especially the chipset used and the drives you use.

I had to change a disk in the past due to incompatibility issues between nforce4 chipsets and maxtor sata2 drives and my problems began a bit like you now.
But my drive sata wasn't damaged just a bit incompatible with the nforce4 sata controller of my MB, it worked perfectly during 6 month then i issued freeze, then BOOT DISK FAILURE with no chance to boot anything from the hardrive. I replaced the disk by a IDE then all is good now and i use this same sata drive in a external box through usb without any problem.

---

### Post by A-1337 on 2007-04-18
My motherboard is old Epox 4bea on intel i845 chipset. It's 4 or 5 (or even more) years old and all was fine till now. It couldn't be a hardware incompatiblity that revealed after five years.

Yesterday I've cleaned my box with a vacuum cleaner and it freezes no more. I'll watch over it for a few more days to be sure. No blown capacitors have been spotted.

P. S. How can one check hdd for bad blocks with r/w test? AFAIK fsck.ext3 can perform only read-test.
 Mkfs.ex3 can do it but it will destroy data, right? Is there other solutions then?

---

### Post by frodon on 2007-04-18
I saw also this kind of hardware problem with RAM memory which need to be cleaned especially the connectors. Anyway you did the right things cleaning a computer after 5 years of use is always a good idea.

---

