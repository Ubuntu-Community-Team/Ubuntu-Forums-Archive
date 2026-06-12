---
title: "Limit HDD Capacity Jumper Questions"
date: 2006-09-14
forum: Hardware &amp; Laptops
---

### Post by All Work on 2006-09-14
Hi,

I have a 6.06 installation which I use as a headless webserver, ftp, etc etc. Recently I added two 130GB Seagate Hard Disks in order to use the server to backup other machines on the network.

Unfortunately, the Motherboard and Processor are quite old (2001?) and the system wouldn't boot without having the "Limit Drive Capacity" jumper set (see [http://www.seagate.com/support/kb/disc/ref/jumper_settings.html]("http://www.seagate.com/support/kb/disc/ref/jumper_settings.html")).

Everything else has gone to plan in terms of partitioning and formatting but the disks appear to Ubuntu to be the full 130GB. I've also tried writing more than 32GB to one of the disks with no problems at all.

So, my question is: Will there be any issues with using the full capacity of the disk for storage with this jumper set? And does Ubuntu ignore this jumper and just read the size of the disk directly?

I've not been able to find a real answer to this question so far so any help is really appreciated!

All Work

---

### Post by John.Michael.Kane on 2006-09-14
From what i have read it would seem that it's just a bypass to allow the main board to boot the drive. if ubuntu can see and write 130gb then you should be fine.
Also i would do backup's of that one drive while making sure it's working as it should.

Note: If you can check to see if there's an updated bios for the board.

---

