---
title: "New install : new hardware : disk problems"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by StevenHarper on 2008-12-20
Hi, I have installed and worked with Ubuntu since 6.04, on many computers, but I have a problem with the latest one. (8.10 64bit)

I have a 640Gig Sata3 disk that has 

610Gig Vista Basic
28Gig Ext3
2Gig swap

Grub sits on the MBR, and works, the vista partition was adjusted with a 8.10 64bit live CD.

Now 2 days ago I booted into Ubuntu and got greeted with ext3 errors.

I tried everything to fix them but nothing worked, I assumed that someone (I have kids) had turned it off during the day and broke the partition.  So I re-installed back onto that partition.

Now 2 days after I have the same problem, all the hardware is brand new, so I assume the disk is ok (is there a way to prove this?).

Last time grub never got to "Starting up" now (on the new broken one) I get to the splash screen then : 

```
ata3.00: status ( DRDY ERR }
ata3.00: error: { UNC }
ata3.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x0
ata3.00: BMDMA stat 0x24
ata3.00: cmd 25/00:08:13:ae:e6/00:00:48:00:00/e0 tag 0 dma 4096 in
ata3.00: res 51/40:00:13:ae:36/00:00:48:00:00/e0 Emask 0x9 (media error)
```

this get repeated over and over

occasionally I get (intremingled)
```

end-request I/O error: dev sda: sector 1223077395
EXT3-fs error (device sda5) : ext3_get_inode_loc : <6>ata3: EH complete
```

Now this looks like a bad disk: however its happened twice (I think after shutting down Vista).  Could it be vista munging my ext3 partition with a badly buffered shutdown of the ATA, or is it a broken (brand new) disk?

BTW. I have to type these logs out as they flash past on  the other monitor; not fun - they may have typos.

---

### Post by StevenHarper on 2008-12-20
I get the same Error running a fsck /dev/sda5 off a live CD, they appear in the terminal like there not part of the fsck output.

I have dL'd the Western Digital software to check the disk surface in the meantime - the simple test passed, but I have set it on a full scan.  I have also got a newer Bios for my Gigabye ep45c ds3r (r4 from r2), but I have yet to try that.

---

### Post by StevenHarper on 2008-12-20
Ok : result : it's what I feared, the brand new disk has lots of bad sectors from the 1,210,000,000 block onward.

The western digital full disk scan utility shows that up.

---

### Post by wolf996 on 2009-01-04
I presume that a new disk solved your problems?

I have been fixing up my baby-sitters PC, which was running Windows XP.  Each time I would get it working it would come back corrupted again some time later.  This corruption also extended to the protected disk area where the backup OS was stored, so a restore was not an option and, since the original disks were lost, I decided to try Ubuntu intead (she really only needs a browser).

After getting Ubuntu to work I decided to run fsck using the procedure outlined here [http://ubuntuforums.org/showthread.php?t=365714](http://ubuntuforums.org/showthread.php?t=365714) and I get the same problems as you noted above - and lost of them.

I suspect the disk is toast and that is why she keeps getting the corruption.  Trouble is that disks for a laptop are not cheap so she might as well buy a new PC.

Thanks for sharing though - it was nice to see exactly the same error messages showing up in a post.

---

