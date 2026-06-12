---
title: "SATA drives diappearing from running system"
date: 2008-06-17
forum: Hardware
---

### Post by yongjunj on 2008-06-17
Hi all,

I recently set up a FreeNAS virtual machine on VMware Workstation on Hardy Heron (i386). I'm running a (software) RAID 5 array on 4 Samsung 750GB SATA disks (sda, sdb, sdc, sdd on the host Ubuntu). I'm using SOYO KT880 Dragon 2 mobo and Athlon XP 3200+, both pulled from my old system.

The RAID array works beautifully, except that every once in a while (more than once a week) a drive would just disappear from a running system and degrade the array. The troubling drive disappears from the host Ubuntu, and hence the FreeNAS virtual machine is unable to access it. The missing drive reappears upon reboot, and everything's fine again once the rebuild process finishes.

And it's not just one specific drive that keeps disappearing; about two days ago, I had /dev/sdc disappear on me, and today /dev/sdb. I've tried running FreeNAS natively also (It's based on FreeBSD 6.2), and it didn't resolve the issue. One drive would still go missing and reappear upon reboot.

I bought the HDDs just 2 weeks ago, so I doubt that it's failing HDDs. At this point, I'm wondering if it's the mobo crapping on me as a whole, as opposed to just one SATA controller going bad. FYI, the mobo has 2 different SATA controllers - VIA VT8237, which handles /dev/sda and /dev/sdb; and ALi M5281, which handles /dev/sdc and /dev/sdd.

I've looked at the dmesg log, and I did notice that I'm getting a lot of "ATA bus errors", and the system eventually gives up resetting the link and just disables it.

What do you guys think? Do you think it's hardware problem (the mobo, to be specific), or some Linux driver issue? I've never had this problem in my old system - I had one 200GB Seagate HDD on VT8237 and no other HDDs.

The following is what I think is the interesting part of the dmesg log on the host Ubuntu. I'm also attaching the full dmesg log.

Any help or comment would be greatly appreciated.

Thx,
Jun

======================================================

[51350.586091] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[51350.586546] sd 0:0:0:0: [sda] Write Protect is off
[51350.586550] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[51350.590209] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[51381.305979] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[51381.305996] ata2.00: BMDMA stat 0x85
[51381.306004] ata2.00: cmd 35/00:e8:00:48:4d/00:01:0f:00:00/e0 tag 0 dma 249856 out
[51381.306006]          res 51/84:9a:4e:48:4d/84:01:0f:00:00/e0 Emask 0x10 (ATA bus error)
[51381.306012] ata2.00: status: { DRDY ERR }
[51381.306016] ata2.00: error: { ICRC ABRT }
[51381.307949] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[51381.307963] ata1.00: BMDMA stat 0x85
[51381.307971] ata1.00: cmd 35/00:20:e0:46:4d/00:01:0f:00:00/e0 tag 0 dma 147456 out
[51381.307973]          res 51/84:b9:47:47:4d/84:00:0f:00:00/e0 Emask 0x10 (ATA bus error)
[51381.307979] ata1.00: status: { DRDY ERR }
[51381.307983] ata1.00: error: { ICRC ABRT }
[51381.615435] ata2: soft resetting link
[51381.623521] ata1: soft resetting link
[51381.771330] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[51381.779321] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[51381.795705] ata2.00: configured for UDMA/133
[51381.795728] ata2: EH complete
[51381.799946] sd 1:0:0:0: [sdb] 1465149168 512-byte hardware sectors (750156 MB)
[51381.801370] sd 1:0:0:0: [sdb] Write Protect is off
[51381.801378] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[51381.802164] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[51381.804621] ata1.00: configured for UDMA/133
[51381.804638] ata1: EH complete
[51381.809977] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[51381.810013] sd 0:0:0:0: [sda] Write Protect is off
[51381.810016] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[51381.810036] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[51863.808932] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2
[51863.808948] ata1.00: BMDMA stat 0x85
[51863.808957] ata1.00: cmd 35/00:00:00:17:53/00:04:0f:00:00/e0 tag 0 dma 524288 out
[51863.808958]          res 51/84:6c:94:18:53/84:02:0f:00:00/e0 Emask 0x10 (ATA bus error)
[51863.808965] ata1.00: status: { DRDY ERR }
[51863.808969] ata1.00: error: { ICRC ABRT }
[51864.117031] ata1: soft resetting link
[51864.272897] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[51864.289452] ata1.00: configured for UDMA/133
[51864.289472] ata1: EH complete
[51864.297463] sd 0:0:0:0: [sda] 1465149168 512-byte hardware sectors (750156 MB)
[51864.297487] sd 0:0:0:0: [sda] Write Protect is off
[51864.297489] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[51864.297833] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[55035.329238] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x400000 action 0x2 frozen
[55035.329257] ata2: SError: { Handshk }
[55035.329264] ata2.00: cmd 35/00:00:00:93:8e/00:04:0f:00:00/e0 tag 0 dma 524288 out
[55035.329266]          res 40/00:9a:4e:48:4d/84:01:0f:00:00/e0 Emask 0x4 (timeout)
[55035.329273] ata2.00: status: { DRDY }
[55040.676658] ata2: port is slow to respond, please be patient (Status 0xd0)
[55045.376608] ata2: device not ready (errno=-16), forcing hardreset
[55045.376616] ata2: hard resetting link
[55050.887874] ata2: port is slow to respond, please be patient (Status 0xd0)
[55055.420014] ata2: COMRESET failed (errno=-16)
[55055.420031] ata2: hard resetting link
[55060.931226] ata2: port is slow to respond, please be patient (Status 0xd0)
[55065.463363] ata2: COMRESET failed (errno=-16)
[55065.463380] ata2: hard resetting link
[55070.974640] ata2: port is slow to respond, please be patient (Status 0xd0)
[55100.473260] ata2: COMRESET failed (errno=-16)
[55100.473278] ata2: limiting SATA link speed to 1.5 Gbps
[55100.473280] ata2: hard resetting link
[55105.480990] ata2: COMRESET failed (errno=-16)
[55105.481007] ata2: reset failed, giving up
[55105.481012] ata2.00: disabled
[55105.481031] ata2: EH complete
[55105.481826] sd 1:0:0:0: [sdb] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[55105.481833] end_request: I/O error, dev sdb, sector 261001984
[55105.481836] printk: 4 messages suppressed.
[55105.481839] Buffer I/O error on device sdb, logical block 32625248
[55105.481844] lost page write due to I/O error on sdb
[55105.481853] Buffer I/O error on device sdb, logical block 32625249
[55105.481857] lost page write due to I/O error on sdb

---

### Post by phidia on 2008-06-17
There are some (many?) posts on the web linking/discussing [disappearing drives]("http://www.theinquirer.net/en/inquirer/news/2007/01/25/western-digital-releases-fix-for-vanishing-caviar-drives") and [raids]("http://www.intel.com/support/motherboards/desktop/sb/CS-020811.htm").
I don't know if either of those links is useful but hey you get a free bump. :)

And for whatever it worth here's [my search results]("http://www.google.com/search?q=linux+raid+issues+drives+disappearing&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a").

---

### Post by yongjunj on 2008-06-17
Thanks, phidia. [A little more googling]("http://www.google.com/search?hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&q=%22ata+bus+error%22+%22reset+failed%22+%22giving+up%22&btnG=Search") returned [this post]("http://ubuntuforums.org/showthread.php?t=625076"). Still trying to find a solution...

---

### Post by anibalrojas on 2008-06-22
Edit the kernel entry in the grub starup menu and add the pci=nomsi parameter to the end of it.

--
Aníbal Rojas
[http://laracaraoscura.com](http://laracaraoscura.com)
[http://anibal.rojas.com.ve](http://anibal.rojas.com.ve)

---

### Post by yongjunj on 2008-06-22
Thanks, anibalrojas. I'll try that and post the results.
Could you please explain what pci=nomsi flag does? I've googled, but I can't seem to get a clear documentation on this.

---

### Post by yongjunj on 2008-06-24
I was using the system with the pci=nomsi flag, and I just lost the array again. I'm gonna try to get this hdd replaced and see if that fixes the problem.

---

### Post by yongjunj on 2008-10-31
I just went ahead and replaced the drive, and haven't had any issue since, but in case someone out there is having the same problem, do try changing the SATA cable to the faulting drive first.

I've seen numerous rants about faulty SATA cables on this and other forums. Apparently SATA cables aren't nearly as durable as the good old IDE cables.

And FYI, the above ICRC error I was getting has more to do with the cable; it's the drive reporting that there was a CRC error with the transmitted data.

---

