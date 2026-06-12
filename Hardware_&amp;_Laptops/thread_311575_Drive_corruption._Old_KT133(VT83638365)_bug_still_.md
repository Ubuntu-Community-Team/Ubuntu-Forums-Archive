---
title: "Drive corruption. Old KT133(VT8363/8365) bug still there"
date: 2006-12-03
forum: Hardware &amp; Laptops
---

### Post by watergate on 2006-12-03
Hi!

I just decided to switch my gentoo installation to (k)ubunto 6.10 edgy  and I can see that I have problems with my hdd which gets corrupted due to an old bug in the VT8363/8365 chip.

The problems with the VIA chipsets in windows was solved by new drivers but under linux I don't know. After googling the problem I found that the problem should be with the write buffer under dma mode and if I disable dma the drive works but the performance is terrible. My motherboard is an ABIT KT7 with the latest A9 Bios. On a forum somewere I was told that if you disable "write back cache" in bios the problem should disappear but this option does not seem to be available for the ABIT KT7.

From the /var/log/messages
Nov 30 21:18:12 webserv kernel: [17179628.292000] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Nov 30 21:18:12 webserv kernel: [17179628.292000] hda: dma_intr: error=0x84 { DriveStatusError BadCRC }

 
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 22)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 10)

I'm sure many of you has seen this bug if not now some years ago so please help.

Uname -a:
Linux webserv 2.6.17-10-generic #2 SMP Fri Oct 13 18:45:35 UTC 2006 i686 GNU/Linux

---

### Post by watergate on 2006-12-03
OK I found a workaround. Not the best one but still.

[http://forums.dvdoctor.net/archive/index.php/t-967.html](http://forums.dvdoctor.net/archive/index.php/t-967.html)

Just disable ultra dma mode from the first drive(master) in the IDE chain.

Im using Multi DMA mode now and it's slower but a lot better than PIO mode which made me nuts. should monitor the system a bit more though.

---

