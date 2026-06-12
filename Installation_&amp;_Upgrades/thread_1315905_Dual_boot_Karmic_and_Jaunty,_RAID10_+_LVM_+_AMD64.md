---
title: "Dual boot Karmic and Jaunty, RAID10 + LVM + AMD64"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by 1clue on 2009-11-05
Hi,

This is really about a safe upgrade rather than real dual-boot.  I have an existing setup included below.

I downloaded the alternate image and burned it, but then I started reading the sticky threads about the upgrade, and decided to ask advice.

I have an Intel I7/920 with 6g RAM and an Asus P6T motherboard.  I'm using the on-board SATA controller, but the bios is NOT set up as RAID.

Basically, I have 4 identical disks, configured as RAID all the way through.  There is no non-RAID partition.  I have:
[LIST=1]
[*]MD1 is /boot, raid1 with 4 disks.
[*]MD2 is empty, but small.
[*]MD3 is Gentoo's root partition, RAID1 times 4.
[*]MD4 is nonexistent, I was matching things up by partition to keep my head straight.
[*]MD5 is Ubuntu Jaunty, RAID1 times 4.
[/LIST]

I set up Gentoo thinking that I would be using that most, I used it and loved it years ago.  Now I just don't have time for the maintenance.  I may go back to that at some point, but not right now, and probably not on my main work machine.

What I want to do is install Karmic on MD3, using my shared partitions and also some Karmic-specific ones similar to my existing setup.

I'd like to keep my MD5 Jaunty install runnable until the new OS is working correctly.  I'll share the home directory but not the user home, I'll use different user names and copy my personal files as necessary.

I've seen comment that the normal installer knows RAID now, is that correct?

Any advice on how to proceed?

Thanks.


Existing setup details:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md6 : active raid10 sdb6[1] sdd6[3] sda6[0] sdc6[2]
      1347371264 blocks 64K chunks 2 near-copies [4/4] [UUUU]
      
md5 : active raid1 sdb5[1] sdd5[3] sda5[0] sdc5[2]     / ubuntu
      26225984 blocks [4/4] [UUUU]
      
md3 : active raid1 sdb3[1] sdd3[3] sda3[0] sdc3[2]     / gentoo
      26226048 blocks [4/4] [UUUU]
      
md1 : active raid1 sdd1[3] sdb1[1] sda1[0] sdc1[2]     /boot
      136448 blocks [4/4] [UUUU]

```

```
lvs
  LV               VG   Attr   LSize   Origin Snap%  Move Log Copy%  Convert
  gentoo_distfiles vg   -wi-a-   4.00G
  gentoo_portage   vg   -wi-a-   2.00G
  gentoo_usr       vg   -wi-a-   8.00G
  gentoo_var       vg   -wi-a-   4.00G
  gentoo_vartmp    vg   -wi-a-   6.00G
  shared_archives  vg   -wi-a- 100.00G
  shared_home      vg   -wi-ao  40.00G
  shared_opt       vg   -wi-ao   4.00G
  shared_tmp       vg   -wi-ao   2.00G
  shared_vmware    vg   -wi-ao 120.00G
  ubuntu_usr       vg   -wi-ao   8.00G
  ubuntu_var       vg   -wi-ao   4.00G
  ubuntu_vartmp    vg   -wi-ao   6.00G

```

---

