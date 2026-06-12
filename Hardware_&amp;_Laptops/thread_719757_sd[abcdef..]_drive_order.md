---
title: "sd[abcdef..] drive order"
date: 2008-03-09
forum: Hardware &amp; Laptops
---

### Post by ZioNemo on 2008-03-09
Hi,
my problem is quite simple:
I had just a nice PATA drive (hda == sda) with ubuntu on it.
I just added a new SATA disk to enlarge capacity.
Now my PATA disk is called (hda==sdb) while the new SATA disk is /dev/sda.

Needless to say ubuntu won't boot anymore :(

I found a nice CDimage that enables me to swap the two drives at boot time and thus to boot ubuntu.
This is, however a royal PITA.
I have not been able to find a "clean" way to cope with my problem.
Could someone point me in the Right Direction, pretty please?

I have seen several threads on ubuntu forums dealing wit problems similar to this, but I could not find a real solution.

I would be really interested in some solution that lets me chose the drive to boot from by UUID, instead that using drive letters... especially when they can change like the sdX ones! I could live with the hdX naming scheme where a drive name stays put and does not change when I add something else.

TiA
ZioNemo

---

### Post by logos34 on 2008-03-09
Unless you're on a pre-6.10 ubuntu release, then it should already be using UUIDs, so drive letters shouldn't matter.  Sounds like adding the second drive merely switched the boot order.  But you ought to be able to change that back permanently by simply entering the Bios and resetting the hard disk boot priority.

---

### Post by ZioNemo on 2008-03-09
THANKS!!!
That was it.
I completely overlooked that BIOS setting... and made a fool of myself.

I owe You one :)

Best Regards
ZioNemo

---

