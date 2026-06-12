---
title: "cd/dvd problem"
date: 2016-09-28
forum: Hardware
---

### Post by jgw on 2016-09-28
I have the following dvd installed on my machine.  My problem is that it does not recognize the blank dvd disk (no media).  The dvd disk is brand new and I have tried others, none are recognized.  then I went out and searched for the problem and came across one that said to run K3b setting/configure k3b/devices/setup devices/modify permissions and let it do its thing.  It did that (set them to 666) .  Went back in and the problem persists.  Then, just to make sure, I rebooted but problem remained.  disks tells me that /dev/sr0/ (read only) .

I have no idea what to do next.  I should also mention that the dvd plays stuff just fine.  I also wonder if I should replace the drive.

*-cdrom  
       description: DVD reader
       product: DVD-ROM DH-16D3S
       vendor: PLDS
       physical id: 0.0.0
       bus info: scsi@3:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/sr0
       version: SD11
       capabilities: removable audio dvd
       configuration: ansiversion=5 status=nodisc

---

### Post by iain4626 on 2016-10-11
Perhaps the driver is not even designed to actually record anything onto blanks?
I know I had this problem once with a 2nd hand computer. Someone had sneaked off
with the modern DVD driver and replaced it with an old ancient driver.
Perhaps this link here will be of some help as it mentions a DVD player similar to your own:

[http://www.tomshardware.co.uk/answers/id-2358304/dvd-drive-reading-blank-dvds.html](http://www.tomshardware.co.uk/answers/id-2358304/dvd-drive-reading-blank-dvds.html)

Mind and click on 'See full content'

I guess you've already tried different types of DVD blanks, both + and -

Good luck,

Iain

---

### Post by mcduck on 2016-10-11
Like the drive name & model says, it's a DVD-ROM drive, not a writer.

[https://www.cnet.com/products/liteon-dh-16d3s-dvd-rom-drive-serial-ata-series/specs/]("https://www.cnet.com/products/liteon-dh-16d3s-dvd-rom-drive-serial-ata-series/specs/")

---

