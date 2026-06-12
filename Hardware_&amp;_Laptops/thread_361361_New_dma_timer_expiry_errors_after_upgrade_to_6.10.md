---
title: "New dma_timer_expiry errors after upgrade to 6.10"
date: 2007-02-14
forum: Hardware &amp; Laptops
---

### Post by PhragMunkee on 2007-02-14
I recently upgraded my server from Ubuntu 5.10 to 6.10.  I was running 5.10 with all the updates when I decided to start over with a 6.10 install.  After upgrading to 6.10, I started getting lock-ups when using my software RAID array.  The RAID array is comprised of 5 Seagate 200GB PATA drives on a HPT374 controller running as JBOD.  The errors in the syslog are:
Feb 14 01:32:28 chattalan kernel: [ 9354.336034] hdg: dma_timer_expiry: dma status == 0x21
Feb 14 01:32:29 chattalan kernel: [ 9354.336055] hdi: dma_timer_expiry: dma status == 0x21
Feb 14 01:32:29 chattalan kernel: [ 9354.336062] hdk: dma_timer_expiry: dma status == 0x21
Feb 14 01:32:38 chattalan kernel: [ 9364.333247] hdg: DMA timeout error
Feb 14 01:32:38 chattalan kernel: [ 9364.333275] hdg: dma timeout error: status=0x50 { DriveReady SeekComplete }
Feb 14 01:32:38 chattalan kernel: [ 9364.333284] ide: failed opcode was: unknown
Feb 14 01:32:38 chattalan kernel: [ 9364.333426] hdi: DMA timeout error
Feb 14 01:32:38 chattalan kernel: [ 9364.333435] hdi: dma timeout error: status=0x50 { DriveReady SeekComplete }
Feb 14 01:32:38 chattalan kernel: [ 9364.333442] ide: failed opcode was: unknown
Feb 14 01:32:38 chattalan kernel: [ 9364.333554] hdk: DMA timeout error
Feb 14 01:32:38 chattalan kernel: [ 9364.333562] hdk: dma timeout error: status=0x50 { DriveReady SeekComplete }
Feb 14 01:32:38 chattalan kernel: [ 9364.333569] ide: failed opcode was: unknown
Feb 14 01:32:59 chattalan kernel: [ 9384.863486] hdk: dma_timer_expiry: dma status == 0x21
Feb 14 01:32:59 chattalan kernel: [ 9384.875482] hdg: dma_timer_expiry: dma status == 0x21
Feb 14 01:32:59 chattalan kernel: [ 9384.875498] hdi: dma_timer_expiry: dma status == 0x21

...Time lapse: it locked up and I had to manually restart it when I got back to work...

Feb 14 10:19:35 chattalan syslogd 1.4.1#18ubuntu6: restart.

I checked the last week of syslogs from the 5.10 install that I backed up and there aren't any messages that match a grep on "dma".  And I definitely never had the lock-ups that required physically resetting the server.

Is there something different between 5.10 and 6.10 that could cause those errors to start appearing?

And here's some (hopefully) useful information:
uname -a: Linux chattalan 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 2006 i686 GNU/Linux

Motherboard: Tyan Tiger 230T
Processors: 2x Intel 1GHz P3
RAM: 1.25 GB
Main HDDs: 2x 160GB Seagate SATA on 3Ware 8006 mirrored RAID
Storage HDDs: 5x 200GB Seagate PATA on Highpoint 374 card, configured as JBOD on card and as software RAID 5 in Linux

I'm not sure what other relative information I can post, but let me know if there is anything I can do.

Thank you very, very much in advance!

---

