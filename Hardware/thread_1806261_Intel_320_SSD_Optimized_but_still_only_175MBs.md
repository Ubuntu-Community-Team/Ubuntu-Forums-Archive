---
title: "Intel 320 SSD Optimized but still only 175MB/s"
date: 2011-07-17
forum: Hardware
---

### Post by Paradoxfox93 on 2011-07-17
Update:  Seems hdparm was simply getting it's own rates for its own kind of reads.  I'm getting 280MB/s peak and 160 minimum avg 268MB/s. seems to be either or for different kins of reads.

Can be marked solved or non-issue?  I can't seem to change.


----intro---

So I've just got a new Latop (have yet to update sig will be doing shortly).  It's an Acer BZ602 model (AMD E350).  Came preinstall with Norton brand clickjacker which I dd'd to my desktop (250Gb HD for 40GB of data, ouch, but I have 4Tb).  

Pulled out the HDD and slipped in this slick 40Gb Intel 320.  Comes with a nice little sticker and I love stickers.  This is also my first run @ natty or any upgrade since Lucid.  I'm actually overall very happy with natty and I've some thoughts about it I'll post elsewhere.

---issue---

Anyway, the issue is that benchmarks report the 40Gb attaining ~200-210MB/s.  I'm getting 175MB/s from /dev/sda and 150MB/s from /dev/sda5 (root partition under dm-crypt and LVM) via hdparm -t.  Setup went in like a peach the second time around.  Estimates ~7hrs battery life after three power cycles under active use, 12+ idle.  Suspend should be a truly reasonable alternative to hibernate since I use no swap.  "Active" means web browsing mostly haven't done any games yet)!   The thing originally give 4.5-5hrs  but is rated for 3.5hrs (normal/active I think, I've notice Acer has no inclination to inflate specs with misleading test conditions).

Tweaks Applied:

Enabled, TRIM support with "discard" on all /dev/sda* devices in /etc/fstab as well as noatime

Disabled journalling and enabling writeback cache with

tune2fs -O ^has_journal /dev/sda10

and 

tune2fs -o journal_data_writeback /dev/sda10

Created a Ramdisk in fstab for /tmp

Redirected Firefox cache to /tmp (and don't use any other browsers, it handles Firefox tabs fine).

I also upgraded the RAM from 2Gb to 4Gb.

noop I/O scheduler into rc.local so I can still keep cfq as default for the old HDD to get plugged in via USB.

I thought the noop might be dragging it down but reports are that intels drive controller is strong enough not to need deadline like Jmicron's.

Would it be the encryption slowing it down?

Did I forget something?  MAybe I got a substandard drive?


Alignment was done on 11.04 live with Gparted creating /boot with a 256mb ext2 partition with 1mb preceding.  I originally set everything up with 2mb over some discussion in the intel forums about ebs being 2mb (which sounds rediculous) but all reports are exactly the same.  150/175 rates. After that I booted into the alternate and partitioned sda5, dm-crypt, LVM, install and so on.

Encryption is AES-256  ~50char passphrase (with an excessively random passphrase)

Any ideas?  I will try deadline and see if there's any improvement.

Boot to entering passphrase is ~15s but I haven't compiled a custom kernel for it yet but that should affect these rates should it?  Unlock to desktop is almost unnoticeable (<1s)

Also, it's nice that ubuntu recognizes the encryption like it does standard home folder encryption for the purposes of not having to maintain a keyring (I use keepass2 anyway).

It also tells me "No video device selected" during boot. but it doesn't really seem to be important?

Also if anyone is interested I can write a more extensive report on this laptop.

---

