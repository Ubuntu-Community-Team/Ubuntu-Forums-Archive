---
title: "DVDs can't be read or mounted"
date: 2006-12-18
forum: Hardware &amp; Laptops
---

### Post by yuanhenglizhen on 2006-12-18
Hi everyone,

I had a problem with my dvd multi recorder. After attempting to burn some dvd-r which I failed to do so. The drive was unable to read dvd altogether. Previously the system was able to handle DVDs fine, whether it be reading or writing them. Now the system is having problems recognizing it. 

I'm using Ubuntu 6.06 LTS - Dapper Drake
Below is the output from the dmesg | tail which I think would make sense to the experts here. CDROMs are working fine. It's just the dvd-r and dvd-rw, I wasn't able to mount to even mount them. In gnome, the "CDROM disc" icon appear irregardless of whether the DVD is blank or a written. 

[4310197.306000] hdc: cdrom_decode_status: error=0x40 { LastFailedSense=0x04 }
[4310197.306000] ide: failed opcode was: unknown
[4310197.306000] hdc: ide_intr: huh? expected NULL handler on exit
[4310197.356000] hdc: ATAPI reset complete
[4310197.356000] end_request: I/O error, dev hdc, sector 64
[4310197.356000] isofs_fill_super: bread failed, dev=hdc, iso_blknum=16, block=16
[4310197.386000] hdc: packet command error: status=0x51 { DriveReady SeekComplete Error }
[4310197.386000] hdc: packet command error: error=0x40 { LastFailedSense=0x04 }
[4310197.386000] ide: failed opcode was: unknown
[4310197.395000] hdc: error code: 0x70  sense_key: 0x04  asc: 0x40  ascq: 0x00

I tried searching for information with Google and in this forum but nothing relevant was found. I am also not not sure where I should be looking for in the logs to know what's the problem.

Any help and advise is appreciated, thanks. 

Andy

---

