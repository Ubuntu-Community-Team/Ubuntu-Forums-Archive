---
title: "HDs very slow (not DMA)"
date: 2007-02-13
forum: Hardware &amp; Laptops
---

### Post by HiFish on 2007-02-13
Hi there,
so far i always managed with reading FAQs and HowTos, but now i run into a dead end. Maybe its my rather excentrix system configuration. 
I have a Fileserver (old Athlon 1500+ with 1280 MB Ram) with an Adaptec AAR-2410SA (HW RAID5, 3 x 200 GB) running as sda (this is where ubuntu server 6.06 is installed) and a 3ware Escalade 7810 (HW RAID5, 8 x 160 GB) running as sdb.
Both drives are working so far (and defnitly not as a fake-raid :)) but file acces is very slow, even when copying localy from one to the other (about 5-10 MB/sec).
heres what the hdparm benchmarks says:

```
root@ServhoernchenX4:~# hdparm -Tt /dev/sda

/dev/sda:
 Timing cached reads:   772 MB in  2.00 seconds = 386.00 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
 Timing buffered disk reads:   52 MB in  3.03 seconds =  17.16 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
root@ServhoernchenX4:~# hdparm -Tt /dev/sdb

/dev/sdb:
 Timing cached reads:   808 MB in  2.00 seconds = 404.00 MB/sec
 Timing buffered disk reads:  122 MB in  3.03 seconds =  40.26 MB/sec

```

There also is an Intel Gigabit NIC in there, and if i copy files to my Desktop PC its about 2,5 MB/sec from sda and 10 mb/sec from sdb.
Usually copying through LAN here works at 20-30 MB/sec. 
I realy have no idea what to do to fix that, and hope someone can point me in the right direction.

PS: There are some Pictures over [here]("http://forums.bit-tech.net/showthread.php?t=119388"), as you can see most of the stuff except the 2 raid controllers are standart components.

---

### Post by HiFish on 2007-02-20
Maybe there is some additional information i forgot to post? no suggestions at all? :(

---

### Post by sanitycheck on 2007-03-01
I'd be concerned that those two RAID controllers might not play nice together in the same box, even if you had not noticed the performance problems.  Even controllers of the same make and model don't always work well together.  You have a lot of variables there that a single controller would make disappear.

Just a thought.

---

### Post by HiFish on 2007-03-05
Yeah, but than i had to throw out either all sata or all ide drives, and that would be just sad. I kind-of-fixed it by changin to a Tyan s2460 Motherboard (it has 4 PCI-X slots) and now the transfer speeds are bearable localy and sometimes up to 40 MB/sec in the LAN. Maybe i can get even better results if i tinker abit with which slots i use (due to the space 8 ide cables need there are fewer choices than you might expect with four slots :))
And, after all, trying different motherboards is somewhat cheaper than trying different RAID-controllers :)

---

